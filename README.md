local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

if playerGui:FindFirstChild("CheatExecutorGui") then
	playerGui.CheatExecutorGui:Destroy()
end

-- ГОЛОВНИЙ ІНТЕРФЕЙС
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "CheatExecutorGui"
screenGui.ResetOnSpawn = false
screenGui.DisplayOrder = 999
screenGui.Parent = playerGui

-- ОГОЛОШЕННЯ ЗВЕРХУ ПОСЕРЕДИНІ
local announcementLabel = Instance.new("TextLabel")
announcementLabel.Name = "AnnouncementLabel"
announcementLabel.Size = UDim2.new(0, 500, 0, 45)
announcementLabel.Position = UDim2.new(0.5, -250, 0, 15)
announcementLabel.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
announcementLabel.BackgroundTransparency = 0.2
announcementLabel.BorderSizePixel = 2
announcementLabel.BorderColor3 = Color3.fromRGB(170, 0, 255)
announcementLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
announcementLabel.Text = ""
announcementLabel.Font = Enum.Font.SourceSansBold
announcementLabel.TextSize = 18
announcementLabel.Visible = false
announcementLabel.Parent = screenGui

local cornerAnnounce = Instance.new("UICorner")
cornerAnnounce.CornerRadius = UDim.new(0, 8)
cornerAnnounce.Parent = announcementLabel

local function showAnnouncement(text)
	if text == "" then return end
	announcementLabel.Text = "📢 " .. text
	announcementLabel.Visible = true
	task.wait(3.5)
	announcementLabel.Visible = false
end

local openButton = Instance.new("TextButton")
openButton.Name = "OpenButton"
openButton.Size = UDim2.new(0, 140, 0, 32)
openButton.Position = UDim2.new(0.5, -70, 0, 10)
openButton.BackgroundColor3 = Color3.fromRGB(170, 0, 255)
openButton.BorderSizePixel = 1
openButton.TextColor3 = Color3.fromRGB(255, 255, 255)
openButton.Text = "📂 Open Window"
openButton.Font = Enum.Font.SourceSansBold
openButton.TextSize = 14
openButton.Visible = false
openButton.Parent = screenGui

local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 460, 0, 290)
mainFrame.Position = UDim2.new(0.5, -230, 0.3, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
mainFrame.BorderSizePixel = 1
mainFrame.BorderColor3 = Color3.fromRGB(60, 60, 70)
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.ClipsDescendants = true
mainFrame.Parent = screenGui

local titleLabel = Instance.new("TextLabel")
titleLabel.Size = UDim2.new(0.5, 0, 0, 30)
titleLabel.Position = UDim2.new(0, 10, 0, 0)
titleLabel.BackgroundTransparency = 1
titleLabel.Text = "🧠 Brain Executor"
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.TextXAlignment = Enum.TextXAlignment.Left
titleLabel.Font = Enum.Font.SourceSansBold
titleLabel.TextSize = 16
titleLabel.Parent = mainFrame

local closeButton = Instance.new("TextButton")
closeButton.Size = UDim2.new(0, 30, 0, 22)
closeButton.Position = UDim2.new(1, -30, 0, 4)
closeButton.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
closeButton.BorderSizePixel = 1
closeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
closeButton.Text = "❌"
closeButton.Font = Enum.Font.SourceSansBold
closeButton.TextSize = 13
closeButton.Parent = mainFrame

-- КНОПКИ ВКЛАДОК
local scriptTabBtn = Instance.new("TextButton")
scriptTabBtn.Size = UDim2.new(0, 100, 0, 23)
scriptTabBtn.Position = UDim2.new(0, 10, 0, 35)
scriptTabBtn.BackgroundColor3 = Color3.fromRGB(170, 0, 255)
scriptTabBtn.BorderSizePixel = 1
scriptTabBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
scriptTabBtn.Text = "💻 Script"
scriptTabBtn.Font = Enum.Font.SourceSansBold
scriptTabBtn.TextSize = 11
scriptTabBtn.Parent = mainFrame

local localTabBtn = Instance.new("TextButton")
localTabBtn.Size = UDim2.new(0, 100, 0, 23)
localTabBtn.Position = UDim2.new(0, 10, 0, 60)
localTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
localTabBtn.BorderSizePixel = 1
localTabBtn.TextColor3 = Color3.fromRGB(180, 180, 180)
localTabBtn.Text = "⚡ LocalScript"
localTabBtn.Font = Enum.Font.SourceSansBold
localTabBtn.TextSize = 11
localTabBtn.Parent = mainFrame

local cmdsTabBtn = Instance.new("TextButton")
cmdsTabBtn.Size = UDim2.new(0, 100, 0, 23)
cmdsTabBtn.Position = UDim2.new(0, 10, 0, 85)
cmdsTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
cmdsTabBtn.BorderSizePixel = 1
cmdsTabBtn.TextColor3 = Color3.fromRGB(180, 180, 180)
cmdsTabBtn.Text = "⚙️ Команди"
cmdsTabBtn.Font = Enum.Font.SourceSansBold
cmdsTabBtn.TextSize = 11
cmdsTabBtn.Parent = mainFrame

local playersTabBtn = Instance.new("TextButton")
playersTabBtn.Size = UDim2.new(0, 100, 0, 23)
playersTabBtn.Position = UDim2.new(0, 10, 0, 110)
playersTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
playersTabBtn.BorderSizePixel = 1
playersTabBtn.TextColor3 = Color3.fromRGB(180, 180, 180)
playersTabBtn.Text = "👥 Гравці"
playersTabBtn.Font = Enum.Font.SourceSansBold
playersTabBtn.TextSize = 11
playersTabBtn.Parent = mainFrame

local announceTabBtn = Instance.new("TextButton")
announceTabBtn.Size = UDim2.new(0, 100, 0, 23)
announceTabBtn.Position = UDim2.new(0, 10, 0, 135)
announceTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
announceTabBtn.BorderSizePixel = 1
announceTabBtn.TextColor3 = Color3.fromRGB(180, 180, 180)
announceTabBtn.Text = "📢 Оголошення"
announceTabBtn.Font = Enum.Font.SourceSansBold
announceTabBtn.TextSize = 11
announceTabBtn.Parent = mainFrame

local settingsTabBtn = Instance.new("TextButton")
settingsTabBtn.Size = UDim2.new(0, 100, 0, 23)
settingsTabBtn.Position = UDim2.new(0, 10, 0, 160)
settingsTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
settingsTabBtn.BorderSizePixel = 1
settingsTabBtn.TextColor3 = Color3.fromRGB(180, 180, 180)
settingsTabBtn.Text = "🛠️ Налаштування"
settingsTabBtn.Font = Enum.Font.SourceSansBold
settingsTabBtn.TextSize = 11
settingsTabBtn.Parent = mainFrame

-- 1. КОНТЕЙНЕР ДЛЯ СКРИПТІВ
local scrollContainer = Instance.new("ScrollingFrame")
scrollContainer.Size = UDim2.new(1, -130, 0, 160)
scrollContainer.Position = UDim2.new(0, 120, 0, 35)
scrollContainer.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
scrollContainer.BorderSizePixel = 1
scrollContainer.ScrollBarThickness = 6
scrollContainer.CanvasSize = UDim2.new(0, 800, 0, 1000)
scrollContainer.Parent = mainFrame

local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(1, 0, 1, 0)
textBox.BackgroundTransparency = 1
textBox.TextColor3 = Color3.fromRGB(0, 255, 127)
textBox.Text = ""
textBox.PlaceholderText = "-- Введіть код сюди..."
textBox.TextXAlignment = Enum.TextXAlignment.Left
textBox.TextYAlignment = Enum.TextYAlignment.Top
textBox.ClearTextOnFocus = false
textBox.MultiLine = true
textBox.Font = Enum.Font.Code
textBox.TextSize = 14
textBox.Parent = scrollContainer

-- 2. КОНТЕЙНЕР ДЛЯ КОМАНД
local cmdsFrame = Instance.new("ScrollingFrame")
cmdsFrame.Size = UDim2.new(1, -130, 0, 160)
cmdsFrame.Position = UDim2.new(0, 120, 0, 35)
cmdsFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
cmdsFrame.BorderSizePixel = 1
cmdsFrame.Visible = false
cmdsFrame.CanvasSize = UDim2.new(0, 0, 0, 130)
cmdsFrame.ScrollBarThickness = 6
cmdsFrame.Parent = mainFrame

local infJumpEnabled = false
local infJumpBtn = Instance.new("TextButton")
infJumpBtn.Size = UDim2.new(1, -12, 0, 30)
infJumpBtn.Position = UDim2.new(0, 5, 0, 5)
infJumpBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
infJumpBtn.BorderSizePixel = 1
infJumpBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
infJumpBtn.Text = "🦘 Безкінечний стрибок: OFF"
infJumpBtn.Font = Enum.Font.SourceSansBold
infJumpBtn.TextSize = 13
infJumpBtn.Parent = cmdsFrame

infJumpBtn.MouseButton1Click:Connect(function()
	infJumpEnabled = not infJumpEnabled
	infJumpBtn.Text = infJumpEnabled and "🦘 Безкінечний стрибок: ON" or "🦘 Безкінечний стрибок: OFF"
	infJumpBtn.BackgroundColor3 = infJumpEnabled and Color3.fromRGB(0, 180, 80) or Color3.fromRGB(40, 40, 50)
end)

UserInputService.JumpRequest:Connect(function()
	if infJumpEnabled and player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
		player.Character:FindFirstChildOfClass("Humanoid"):ChangeState(Enum.HumanoidStateType.Jumping)
	end
end)

local speedBox = Instance.new("TextBox")
speedBox.Size = UDim2.new(1, -12, 0, 30)
speedBox.Position = UDim2.new(0, 5, 0, 45)
speedBox.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
speedBox.BorderSizePixel = 1
speedBox.TextColor3 = Color3.fromRGB(0, 255, 127)
speedBox.PlaceholderText = "🏃 Швидкість (наприклад: 50)"
speedBox.Font = Enum.Font.SourceSans
speedBox.TextSize = 13
speedBox.Parent = cmdsFrame

speedBox.FocusLost:Connect(function()
	local num = tonumber(speedBox.Text)
	if num and player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
		player.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = num
	end
end)

local jumpBox = Instance.new("TextBox")
jumpBox.Size = UDim2.new(1, -12, 0, 30)
jumpBox.Position = UDim2.new(0, 5, 0, 85)
jumpBox.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
jumpBox.BorderSizePixel = 1
jumpBox.TextColor3 = Color3.fromRGB(0, 255, 127)
jumpBox.PlaceholderText = "🚀 Сила стрибка (наприклад: 100)"
jumpBox.Font = Enum.Font.SourceSans
jumpBox.TextSize = 13
jumpBox.Parent = cmdsFrame

jumpBox.FocusLost:Connect(function()
	local num = tonumber(jumpBox.Text)
	if num and player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
		local hum = player.Character:FindFirstChildOfClass("Humanoid")
		hum.UseJumpPower = true
		hum.JumpPower = num
	end
end)

-- 3. КОНТЕЙНЕР ДЛЯ ГРАВЦІВ
local playersFrame = Instance.new("ScrollingFrame")
playersFrame.Size = UDim2.new(1, -130, 0, 160)
playersFrame.Position = UDim2.new(0, 120, 0, 35)
playersFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
playersFrame.BorderSizePixel = 1
playersFrame.Visible = false
playersFrame.ScrollBarThickness = 6
playersFrame.Parent = mainFrame

local UIListLayout = Instance.new("UIListLayout")
UIListLayout.Parent = playersFrame
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayout.Padding = UDim.new(0, 4)

local function refreshPlayersList()
	for _, child in ipairs(playersFrame:GetChildren()) do
		if child:IsA("Frame") then child:Destroy() end
	end
	local allPlayers = Players:GetPlayers()
	playersFrame.CanvasSize = UDim2.new(0, 0, 0, #allPlayers * 34)

	for _, p in ipairs(allPlayers) do
		local itemFrame = Instance.new("Frame")
		itemFrame.Size = UDim2.new(1, -10, 0, 30)
		itemFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
		itemFrame.BorderSizePixel = 1
		itemFrame.Parent = playersFrame

		local nameLabel = Instance.new("TextLabel")
		nameLabel.Size = UDim2.new(1, -10, 1, 0)
		nameLabel.Position = UDim2.new(0, 8, 0, 0)
		nameLabel.BackgroundTransparency = 1
		nameLabel.Text = p.DisplayName .. " (@" .. p.Name .. ")"
		nameLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
		nameLabel.TextXAlignment = Enum.TextXAlignment.Left
		nameLabel.Font = Enum.Font.SourceSans
		nameLabel.TextSize = 13
		nameLabel.Parent = itemFrame
	end
end

Players.PlayerAdded:Connect(refreshPlayersList)
Players.PlayerRemoving:Connect(refreshPlayersList)

-- 4. КОНТЕЙНЕР ДЛЯ ОГОЛОШЕНЬ
local announceFrame = Instance.new("Frame")
announceFrame.Size = UDim2.new(1, -130, 0, 160)
announceFrame.Position = UDim2.new(0, 120, 0, 35)
announceFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
announceFrame.BorderSizePixel = 1
announceFrame.Visible = false
announceFrame.Parent = mainFrame

local announceInput = Instance.new("TextBox")
announceInput.Size = UDim2.new(1, -12, 0, 80)
announceInput.Position = UDim2.new(0, 6, 0, 10)
announceInput.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
announceInput.BorderSizePixel = 1
announceInput.TextColor3 = Color3.fromRGB(255, 255, 255)
announceInput.PlaceholderText = "Введіть текст оголошення тут..."
announceInput.Text = ""
announceInput.MultiLine = true
announceInput.Font = Enum.Font.SourceSans
announceInput.TextSize = 14
announceInput.Parent = announceFrame

local announceSendBtn = Instance.new("TextButton")
announceSendBtn.Size = UDim2.new(1, -12, 0, 40)
announceSendBtn.Position = UDim2.new(0, 6, 0, 105)
announceSendBtn.BackgroundColor3 = Color3.fromRGB(170, 0, 255)
announceSendBtn.BorderSizePixel = 1
announceSendBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
announceSendBtn.Text = "📢 Надіслати оголошення"
announceSendBtn.Font = Enum.Font.SourceSansBold
announceSendBtn.TextSize = 14
announceSendBtn.Parent = announceFrame

announceSendBtn.MouseButton1Click:Connect(function()
	if announceInput.Text ~= "" then
		showAnnouncement(announceInput.Text)
	end
end)

-- 5. КОНТЕЙНЕР ДЛЯ НАЛАШТУВАНЬ
local settingsFrame = Instance.new("ScrollingFrame")
settingsFrame.Size = UDim2.new(1, -130, 0, 160)
settingsFrame.Position = UDim2.new(0, 120, 0, 35)
settingsFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
settingsFrame.BorderSizePixel = 1
settingsFrame.Visible = false
settingsFrame.CanvasSize = UDim2.new(0, 0, 0, 160)
settingsFrame.ScrollBarThickness = 6
settingsFrame.Parent = mainFrame

local themeLbl = Instance.new("TextLabel")
themeLbl.Size = UDim2.new(1, -10, 0, 20)
themeLbl.Position = UDim2.new(0, 5, 0, 5)
themeLbl.BackgroundTransparency = 1
themeLbl.Text = "🎨 Колір вікна:"
themeLbl.TextColor3 = Color3.fromRGB(255, 255, 255)
themeLbl.TextXAlignment = Enum.TextXAlignment.Left
themeLbl.Font = Enum.Font.SourceSansBold
themeLbl.TextSize = 12
themeLbl.Parent = settingsFrame

local themeDarkBtn = Instance.new("TextButton")
themeDarkBtn.Size = UDim2.new(0.48, -2, 0, 26)
themeDarkBtn.Position = UDim2.new(0, 5, 0, 28)
themeDarkBtn.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
themeDarkBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
themeDarkBtn.Text = "🌑 Темний"
themeDarkBtn.Font = Enum.Font.SourceSans
themeDarkBtn.TextSize = 12
themeDarkBtn.Parent = settingsFrame

local themePurpleBtn = Instance.new("TextButton")
themePurpleBtn.Size = UDim2.new(0.48, -2, 0, 26)
themePurpleBtn.Position = UDim2.new(0.5, 2, 0, 28)
themePurpleBtn.BackgroundColor3 = Color3.fromRGB(50, 20, 70)
themePurpleBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
themePurpleBtn.Text = "🟣 Фіолетовий"
themePurpleBtn.Font = Enum.Font.SourceSans
themePurpleBtn.TextSize = 12
themePurpleBtn.Parent = settingsFrame

themeDarkBtn.MouseButton1Click:Connect(function()
	mainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
end)

themePurpleBtn.MouseButton1Click:Connect(function()
	mainFrame.BackgroundColor3 = Color3.fromRGB(45, 20, 65)
end)

local fontLbl = Instance.new("TextLabel")
fontLbl.Size = UDim2.new(1, -10, 0, 20)
fontLbl.Position = UDim2.new(0, 5, 0, 62)
fontLbl.BackgroundTransparency = 1
fontLbl.Text = "🔤 Шрифт коду:"
fontLbl.TextColor3 = Color3.fromRGB(255, 255, 255)
fontLbl.TextXAlignment = Enum.TextXAlignment.Left
fontLbl.Font = Enum.Font.SourceSansBold
fontLbl.TextSize = 12
fontLbl.Parent = settingsFrame

local fontCodeBtn = Instance.new("TextButton")
fontCodeBtn.Size = UDim2.new(0.48, -2, 0, 26)
fontCodeBtn.Position = UDim2.new(0, 5, 0, 85)
fontCodeBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
fontCodeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
fontCodeBtn.Text = "Code (Моно)"
fontCodeBtn.Font = Enum.Font.SourceSans
fontCodeBtn.TextSize = 12
fontCodeBtn.Parent = settingsFrame

local fontGothamBtn = Instance.new("TextButton")
fontGothamBtn.Size = UDim2.new(0.48, -2, 0, 26)
fontGothamBtn.Position = UDim2.new(0.5, 2, 0, 85)
fontGothamBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
fontGothamBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
fontGothamBtn.Text = "Gotham"
fontGothamBtn.Font = Enum.Font.SourceSans
fontGothamBtn.TextSize = 12
fontGothamBtn.Parent = settingsFrame

fontCodeBtn.MouseButton1Click:Connect(function()
	textBox.Font = Enum.Font.Code
end)

fontGothamBtn.MouseButton1Click:Connect(function()
	textBox.Font = Enum.Font.Gotham
end)

-- НИЖНІ КНОПКИ
local clearButton = Instance.new("TextButton")
clearButton.Size = UDim2.new(0, 90, 0, 35)
clearButton.Position = UDim2.new(0, 120, 0, 205)
clearButton.BackgroundColor3 = Color3.fromRGB(200, 80, 0)
clearButton.BorderSizePixel = 1
clearButton.TextColor3 = Color3.fromRGB(255, 255, 255)
clearButton.Text = "🗑️ Очистити"
clearButton.Font = Enum.Font.SourceSansBold
clearButton.TextSize = 13
clearButton.Parent = mainFrame

local executeButton = Instance.new("TextButton")
executeButton.Size = UDim2.new(0, 220, 0, 35)
executeButton.Position = UDim2.new(1, -230, 0, 205)
executeButton.BackgroundColor3 = Color3.fromRGB(170, 0, 255)
executeButton.BorderSizePixel = 1
executeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
executeButton.Text = "⚡ Запустити Script"
executeButton.Font = Enum.Font.SourceSansBold
executeButton.TextSize = 14
executeButton.Parent = mainFrame

-- ПЕРЕМИКАННЯ РЕЖИМІВ
local currentMode = "Script"

local function setMode(mode)
	currentMode = mode
	scriptTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
	localTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
	cmdsTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
	playersTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
	announceTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)
	settingsTabBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 55)

	scrollContainer.Visible = false
	cmdsFrame.Visible = false
	playersFrame.Visible = false
	announceFrame.Visible = false
	settingsFrame.Visible = false
	clearButton.Visible = true
	executeButton.Visible = true

	if mode == "Script" then
		scriptTabBtn.BackgroundColor3 = Color3.fromRGB(170, 0, 255)
		executeButton.BackgroundColor3 = Color3.fromRGB(170, 0, 255)
		executeButton.Text = "⚡ Запустити Script"
		scrollContainer.Visible = true
	elseif mode == "LocalScript" then
		localTabBtn.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
		executeButton.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
		executeButton.Text = "⚡ Запустити Local"
		scrollContainer.Visible = true
	elseif mode == "Cmds" then
		cmdsTabBtn.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
		clearButton.Visible = false
		executeButton.Visible = false
		cmdsFrame.Visible = true
	elseif mode == "Players" then
		playersTabBtn.BackgroundColor3 = Color3.fromRGB(220, 50, 50)
		clearButton.Visible = false
		executeButton.Visible = false
		playersFrame.Visible = true
		refreshPlayersList()
	elseif mode == "Announce" then
		announceTabBtn.BackgroundColor3 = Color3.fromRGB(255, 140, 0)
		clearButton.Visible = false
		executeButton.Visible = false
		announceFrame.Visible = true
	elseif mode == "Settings" then
		settingsTabBtn.BackgroundColor3 = Color3.fromRGB(120, 120, 140)
		clearButton.Visible = false
		executeButton.Visible = false
		settingsFrame.Visible = true
	end
end

scriptTabBtn.MouseButton1Click:Connect(function() setMode("Script") end)
localTabBtn.MouseButton1Click:Connect(function() setMode("LocalScript") end)
cmdsTabBtn.MouseButton1Click:Connect(function() setMode("Cmds") end)
playersTabBtn.MouseButton1Click:Connect(function() setMode("Players") end)
announceTabBtn.MouseButton1Click:Connect(function() setMode("Announce") end)
settingsTabBtn.MouseButton1Click:Connect(function() setMode("Settings") end)

clearButton.MouseButton1Click:Connect(function()
	textBox.Text = ""
end)

closeButton.MouseButton1Click:Connect(function()
	mainFrame.Visible = false
	openButton.Visible = true
end)

openButton.MouseButton1Click:Connect(function()
	mainFrame.Visible = true
	openButton.Visible = false
end)

executeButton.MouseButton1Click:Connect(function()
	if textBox.Text ~= "" then
		local fn, err = loadstring(textBox.Text)
		if fn then
			task.spawn(fn)
		else
			warn("[Execution Error]: " .. tostring(err))
		end
	end
end)
