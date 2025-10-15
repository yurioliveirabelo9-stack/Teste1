# -- H4x Hub (Painel Transparente Cinza com textos brancos)
-- Feito para Delta Executor - Roblox

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

if PlayerGui:FindFirstChild("H4xHub_GUI") then
	PlayerGui.H4xHub_GUI:Destroy()
end

local function new(inst, props)
	local obj = Instance.new(inst)
	for k,v in pairs(props or {}) do
		obj[k] = v
	end
	return obj
end

-- GUI principal
local gui = new("ScreenGui", {
	Name = "H4xHub_GUI",
	Parent = PlayerGui,
	ResetOnSpawn = false
})

local main = new("Frame", {
	Parent = gui,
	AnchorPoint = Vector2.new(0.5,0.5),
	Position = UDim2.new(0.5,0,0.5,0),
	Size = UDim2.new(0,520,0,320),
	BackgroundColor3 = Color3.fromRGB(50,50,50),
	BackgroundTransparency = 0.35, -- transparente cinza
	BorderSizePixel = 0,
})
new("UICorner", {Parent = main, CornerRadius = UDim.new(0,10)})

-- Barra superior
local topBar = new("Frame", {
	Parent = main,
	Size = UDim2.new(1,0,0,36),
	BackgroundTransparency = 1,
})
local title = new("TextLabel", {
	Parent = topBar,
	Text = "H4x Hub",
	Font = Enum.Font.SourceSansBold,
	TextSize = 20,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundTransparency = 1,
	Position = UDim2.new(0,10,0,0),
	Size = UDim2.new(1,-50,1,0),
	TextXAlignment = Enum.TextXAlignment.Left
})

local closeBtn = new("TextButton", {
	Parent = topBar,
	Text = "X",
	Font = Enum.Font.SourceSansBold,
	TextSize = 18,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundColor3 = Color3.fromRGB(120,50,50),
	BackgroundTransparency = 0.25,
	Size = UDim2.new(0,36,0,24),
	Position = UDim2.new(1,-46,0,6),
})
new("UICorner", {Parent = closeBtn, CornerRadius = UDim.new(0,6)})
closeBtn.MouseButton1Click:Connect(function() gui:Destroy() end)

-- Menu esquerdo
local left = new("Frame", {
	Parent = main,
	Size = UDim2.new(0,160,1,-36),
	Position = UDim2.new(0,0,0,36),
	BackgroundColor3 = Color3.fromRGB(60,60,60),
	BackgroundTransparency = 0.4,
})
new("UICorner", {Parent = left, CornerRadius = UDim.new(0,8)})

local list = new("UIListLayout", {
	Parent = left,
	Padding = UDim.new(0,8),
	SortOrder = Enum.SortOrder.LayoutOrder,
	HorizontalAlignment = Enum.HorizontalAlignment.Center,
})

local function createButton(name)
	local btn = new("TextButton", {
		Parent = left,
		Text = name,
		Font = Enum.Font.SourceSansBold,
		TextSize = 16,
		TextColor3 = Color3.fromRGB(255,255,255),
		BackgroundColor3 = Color3.fromRGB(80,80,80),
		BackgroundTransparency = 0.4,
		Size = UDim2.new(0.9,0,0,36),
	})
	new("UICorner", {Parent = btn, CornerRadius = UDim.new(0,8)})
	return btn
end

local btnSpeedJump = createButton("Speed and Jump")

-- Painel direito
local right = new("Frame", {
	Parent = main,
	Position = UDim2.new(0,160,0,36),
	Size = UDim2.new(1,-160,1,-36),
	BackgroundColor3 = Color3.fromRGB(70,70,70),
	BackgroundTransparency = 0.45,
})
new("UICorner", {Parent = right, CornerRadius = UDim.new(0,8)})

local scroll = new("ScrollingFrame", {
	Parent = right,
	Size = UDim2.new(1,-10,1,-10),
	Position = UDim2.new(0,5,0,5),
	CanvasSize = UDim2.new(0,0,0,0),
	ScrollBarThickness = 6,
	BackgroundTransparency = 1,
})
local layout = new("UIListLayout", {
	Parent = scroll,
	Padding = UDim.new(0,10),
	SortOrder = Enum.SortOrder.LayoutOrder,
})

-- Função atualizar rolagem
local function updateCanvas()
	task.wait()
	scroll.CanvasSize = UDim2.new(0,0,0,layout.AbsoluteContentSize + 10)
end

-- Conteúdo: Speed & Jump
local frame = new("Frame", {
	Parent = scroll,
	Size = UDim2.new(1, -10, 0, 220),
	BackgroundColor3 = Color3.fromRGB(90,90,90),
	BackgroundTransparency = 0.45,
})
new("UICorner", {Parent = frame, CornerRadius = UDim.new(0,8)})

local title2 = new("TextLabel", {
	Parent = frame,
	Text = "Speed & Jump",
	Font = Enum.Font.SourceSansBold,
	TextSize = 18,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundTransparency = 1,
	Position = UDim2.new(0,10,0,10),
	Size = UDim2.new(1,-20,0,26),
	TextXAlignment = Enum.TextXAlignment.Left,
})

-- Campo de velocidade
local speedLabel = new("TextLabel", {
	Parent = frame,
	Text = "Velocidade (WalkSpeed):",
	Font = Enum.Font.SourceSans,
	TextSize = 14,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundTransparency = 1,
	Position = UDim2.new(0,10,0,46),
	Size = UDim2.new(1,-20,0,20),
	TextXAlignment = Enum.TextXAlignment.Left,
})
local speedBox = new("TextBox", {
	Parent = frame,
	Text = "16",
	Font = Enum.Font.SourceSans,
	TextSize = 16,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundColor3 = Color3.fromRGB(120,120,120),
	BackgroundTransparency = 0.4,
	Position = UDim2.new(0,10,0,68),
	Size = UDim2.new(0.6,0,0,36),
	ClearTextOnFocus = false,
})
new("UICorner", {Parent = speedBox, CornerRadius = UDim.new(0,6)})

local applySpeed = new("TextButton", {
	Parent = frame,
	Text = "Aplicar Velocidade",
	Font = Enum.Font.SourceSansBold,
	TextSize = 14,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundColor3 = Color3.fromRGB(100,150,255),
	BackgroundTransparency = 0.25,
	Position = UDim2.new(0.62,0,0,68),
	Size = UDim2.new(0.36,0,0,36),
})
new("UICorner", {Parent = applySpeed, CornerRadius = UDim.new(0,6)})

-- Campo de pulo
local jumpLabel = new("TextLabel", {
	Parent = frame,
	Text = "Pulo (JumpPower):",
	Font = Enum.Font.SourceSans,
	TextSize = 14,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundTransparency = 1,
	Position = UDim2.new(0,10,0,120),
	Size = UDim2.new(1,-20,0,20),
	TextXAlignment = Enum.TextXAlignment.Left,
})
local jumpBox = new("TextBox", {
	Parent = frame,
	Text = "50",
	Font = Enum.Font.SourceSans,
	TextSize = 16,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundColor3 = Color3.fromRGB(120,120,120),
	BackgroundTransparency = 0.4,
	Position = UDim2.new(0,10,0,142),
	Size = UDim2.new(0.6,0,0,36),
	ClearTextOnFocus = false,
})
new("UICorner", {Parent = jumpBox, CornerRadius = UDim.new(0,6)})

local applyJump = new("TextButton", {
	Parent = frame,
	Text = "Aplicar Pulo",
	Font = Enum.Font.SourceSansBold,
	TextSize = 14,
	TextColor3 = Color3.fromRGB(255,255,255),
	BackgroundColor3 = Color3.fromRGB(120,255,150),
	BackgroundTransparency = 0.25,
	Position = UDim2.new(0.62,0,0,142),
	Size = UDim2.new(0.36,0,0,36),
})
new("UICorner", {Parent = applyJump, CornerRadius = UDim.new(0,6)})

-- Funções de aplicar
local function getHumanoid()
	local c = LocalPlayer.Character
	return c and c:FindFirstChildOfClass("Humanoid")
end

applySpeed.MouseButton1Click:Connect(function()
	local val = tonumber(speedBox.Text)
	local hum = getHumanoid()
	if hum and val then
		hum.WalkSpeed = val
		applySpeed.Text = "✔ Aplicado"
		task.wait(1)
		applySpeed.Text = "Aplicar Velocidade"
	end
end)

applyJump.MouseButton1Click:Connect(function()
	local val = tonumber(jumpBox.Text)
	local hum = getHumanoid()
	if hum and val then
		hum.JumpPower = val
		hum.UseJumpPower = true
		applyJump.Text = "✔ Aplicado"
		task.wait(1)
		applyJump.Text = "Aplicar Pulo"
	end
end)

-- Atualiza canvas
updateCanvas()

-- Arrastar o painel
do
	local dragging, dragStart, startPos, dragInput
	main.InputBegan:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
			dragging = true
			dragStart = input.Position
			startPos = main.Position
			input.Changed:Connect(function()
				if input.UserInputState == Enum.UserInputState.End then
					dragging = false
				end
			end)
		end
	end)
	main.InputChanged:Connect(function(input)
		if input == dragInput and dragging then
			local delta = input.Position - dragStart
			main.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
		end
	end)
	game:GetService("UserInputService").InputChanged:Connect(function(input)
		if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
			local delta = input.Position - dragStart
			main.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
		end
	end)
end
