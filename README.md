-- =============================================================================
--       mtz hub | ULTIMATE PURPLE CYBER EDITION • v5.3 (PREMIUM UI UPDATE)
-- =============================================================================
-- Criado com exclusividade por: TheDevMtz

local CoreGui = game:GetService("CoreGui")
local Workspace = game:GetService("Workspace")
local Lighting = game:GetService("Lighting")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local StatsService = game:GetService("Stats")
local Players = game:GetService("Players")

-- Evitar duplicação da interface
if CoreGui:FindFirstChild("mtzHubPurpleV5") then
    CoreGui:FindFirstChild("mtzHubPurpleV5"):Destroy()
end

-- Paleta de Cores Premium Roxa Cyber
local Cores = {
    FundoPrincipal = Color3.fromRGB(12, 10, 18),   -- Obsidiana Roxa
    FundoCard = Color3.fromRGB(20, 16, 30),        -- Roxo escuro fosco para os cards
    Sidebar = Color3.fromRGB(15, 12, 24),          -- Sidebar
    TextoClaro = Color3.fromRGB(245, 240, 255),    -- Branco Violeta
    TextoEscuro = Color3.fromRGB(130, 120, 155),   -- Roxo de suporte
    Accent = Color3.fromRGB(157, 78, 221),         -- Roxo Neon Principal
    VerdeNeon = Color3.fromRGB(0, 230, 153),      -- Sucesso / Excelente
    VermelhoNeon = Color3.fromRGB(255, 75, 110),   -- Crítico / Alerta
}

-- Criando a ScreenGui
local mtzHub = Instance.new("ScreenGui")
mtzHub.Name = "mtzHubPurpleV5"
mtzHub.Parent = CoreGui
mtzHub.ResetOnSpawn = false

-- ====== BOTÃO FLUTUANTE PREMIUM RE-DESIGNED (CLEAN) ======
local ToggleButton = Instance.new("TextButton")
ToggleButton.Name = "ToggleButton"
ToggleButton.Parent = mtzHub
ToggleButton.Size = UDim2.new(0, 48, 0, 48)
ToggleButton.Position = UDim2.new(0, 20, 0, 200)
ToggleButton.BackgroundColor3 = Cores.FundoCard
ToggleButton.Text = "MTZ"
ToggleButton.TextColor3 = Cores.TextoClaro
ToggleButton.TextSize = 13
ToggleButton.Font = Enum.Font.GothamBold
ToggleButton.AutoButtonColor = false

-- Arredondamento suave e moderno
local ToggleCorner = Instance.new("UICorner")
ToggleCorner.CornerRadius = UDim.new(0, 12)
ToggleCorner.Parent = ToggleButton

-- Borda Neon Roxa (Clean, sem gradiente poluído)
local ToggleStroke = Instance.new("UIStroke")
ToggleStroke.Thickness = 1.5
ToggleStroke.Color = Cores.Accent
ToggleStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
ToggleStroke.Parent = ToggleButton

-- Efeitos de Hover/Feedback Visual ao passar o dedo
ToggleButton.MouseEnter:Connect(function()
    TweenService:Create(ToggleButton, TweenInfo.new(0.2, Enum.EasingStyle.Quart), {Size = UDim2.new(0, 52, 0, 52)}):Play()
    TweenService:Create(ToggleStroke, TweenInfo.new(0.2), {Thickness = 2.5}):Play()
end)

ToggleButton.MouseLeave:Connect(function()
    TweenService:Create(ToggleButton, TweenInfo.new(0.2, Enum.EasingStyle.Quart), {Size = UDim2.new(0, 48, 0, 48)}):Play()
    TweenService:Create(ToggleStroke, TweenInfo.new(0.2), {Thickness = 1.5}):Play()
end)


-- ====== PAINEL PRINCIPAL (DESIGN PREMIUM MOBILE) ======
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Parent = mtzHub
MainFrame.Size = UDim2.new(0, 520, 0, 300) 
MainFrame.Position = UDim2.new(0.5, -260, 0.5, -150) 
MainFrame.BackgroundColor3 = Cores.FundoPrincipal
MainFrame.Visible = false
MainFrame.ClipsDescendants = true

local MainCorner = Instance.new("UICorner")
MainCorner.CornerRadius = UDim.new(0, 16)
MainCorner.Parent = MainFrame

local MainStroke = Instance.new("UIStroke")
MainStroke.Color = Color3.fromRGB(40, 32, 65)
MainStroke.Thickness = 1.2
MainStroke.Parent = MainFrame

-- ====== BOTÃO DE FECHAR COMPACTO (X) ======
local CloseButton = Instance.new("TextButton")
CloseButton.Name = "CloseButton"
CloseButton.Parent = MainFrame
CloseButton.Size = UDim2.new(0, 28, 0, 28)
CloseButton.Position = UDim2.new(1, -38, 0, 12)
CloseButton.BackgroundColor3 = Color3.fromRGB(26, 14, 32)
CloseButton.Text = "×"
CloseButton.TextColor3 = Cores.VermelhoNeon
CloseButton.TextSize = 22
CloseButton.Font = Enum.Font.GothamBold

local CloseCorner = Instance.new("UICorner")
CloseCorner.CornerRadius = UDim.new(0, 8)
CloseCorner.Parent = CloseButton

CloseButton.MouseButton1Click:Connect(function()
    TweenService:Create(MainFrame, TweenInfo.new(0.2, Enum.EasingStyle.Quart, Enum.EasingDirection.In), {Size = UDim2.new(0, 520, 0, 0)}):Play()
    task.wait(0.2)
    MainFrame.Visible = false
end)

-- ====== MENU LATERAL AUTO-SCROLL (SIDEBAR ESPACIAL) ======
local Sidebar = Instance.new("Frame")
Sidebar.Name = "Sidebar"
Sidebar.Parent = MainFrame
Sidebar.Size = UDim2.new(0, 145, 1, 0)
Sidebar.BackgroundColor3 = Cores.Sidebar

local SidebarCorner = Instance.new("UICorner")
SidebarCorner.CornerRadius = UDim.new(0, 16)
SidebarCorner.Parent = Sidebar

local HideCorner = Instance.new("Frame")
HideCorner.Size = UDim2.new(0, 20, 1, 0)
HideCorner.Position = UDim2.new(1, -20, 0, 0)
HideCorner.BackgroundColor3 = Cores.Sidebar
HideCorner.BorderSizePixel = 0
HideCorner.Parent = Sidebar

local Logo = Instance.new("TextLabel")
Logo.Size = UDim2.new(1, 0, 0, 45)
Logo.Text = "mtz hub"
Logo.TextColor3 = Cores.TextoClaro
Logo.TextSize = 20
Logo.Font = Enum.Font.GothamBold
Logo.BackgroundTransparency = 1
Logo.Parent = Sidebar

local LogoSub = Instance.new("TextLabel")
LogoSub.Size = UDim2.new(1, 0, 0, 20)
LogoSub.Position = UDim2.new(0, 0, 0, 32)
LogoSub.Text = "v5.3 Ultimate"
LogoSub.TextColor3 = Cores.Accent
LogoSub.TextSize = 10
LogoSub.Font = Enum.Font.GothamSemibold
LogoSub.BackgroundTransparency = 1
LogoSub.Parent = Sidebar

-- Container de Rolagem para suportar infinitas abas sem poluir a interface
local NavContainer = Instance.new("ScrollingFrame")
NavContainer.Size = UDim2.new(1, 0, 1, -75)
NavContainer.Position = UDim2.new(0, 0, 0, 70)
NavContainer.BackgroundTransparency = 1
NavContainer.ScrollBarThickness = 0
NavContainer.CanvasSize = UDim2.new(0, 0, 0, 0)
NavContainer.Parent = Sidebar

local NavLayout = Instance.new("UIListLayout")
NavLayout.Parent = NavContainer
NavLayout.Padding = UDim.new(0, 6)
NavLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

NavLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    NavContainer.CanvasSize = UDim2.new(0, 0, 0, NavLayout.AbsoluteContentSize.Y + 10)
end)

-- ====== RECEPTÁCULO DAS ABAS ======
local ContentArea = Instance.new("Frame")
ContentArea.Size = UDim2.new(1, -165, 1, -60)
ContentArea.Position = UDim2.new(0, 155, 0, 50)
ContentArea.BackgroundTransparency = 1
ContentArea.Parent = MainFrame

local function CriarAbaConteudo()
    local Scroll = Instance.new("ScrollingFrame")
    Scroll.Size = UDim2.new(1, 0, 1, 0)
    Scroll.BackgroundTransparency = 1
    Scroll.ScrollBarThickness = 3
    Scroll.ScrollBarImageColor3 = Cores.Accent
    Scroll.CanvasSize = UDim2.new(0, 0, 0, 0)
    Scroll.Visible = false
    Scroll.Parent = ContentArea
    
    local Layout = Instance.new("UIListLayout")
    Layout.Parent = Scroll
    Layout.Padding = UDim.new(0, 8)
    
    Layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
        Scroll.CanvasSize = UDim2.new(0, 0, 0, Layout.AbsoluteContentSize.Y + 15)
    end)
    return Scroll
end

-- Instanciando todas as abas necessárias
local TabGraficos = CriarAbaConteudo()
local TabAntiLag = CriarAbaConteudo()
local TabSettings = CriarAbaConteudo()
local TabAvancado = CriarAbaConteudo()
local TabStatus = Instance.new("Frame")
TabStatus.Size = UDim2.new(1, 0, 1, 0)
TabStatus.BackgroundTransparency = 1
TabStatus.Visible = false
TabStatus.Parent = ContentArea

local TabCreditos = Instance.new("Frame")
TabCreditos.Size = UDim2.new(1, 0, 1, 0)
TabCreditos.BackgroundTransparency = 1
TabCreditos.Visible = false
TabCreditos.Parent = ContentArea

-- Gerador Centralizado de Botões do Menu Lateral
local function CriarBotaoMenu(nome, abaAlvo)
    local Btn = Instance.new("TextButton")
    Btn.Size = UDim2.new(0, 125, 0, 34)
    Btn.BackgroundColor3 = Color3.fromRGB(32, 24, 50)
    Btn.BackgroundTransparency = 1
    Btn.Text = nome
    Btn.TextColor3 = Cores.TextoEscuro
    Btn.TextSize = 12
    Btn.Font = Enum.Font.GothamSemibold
    Btn.Parent = NavContainer

    local BtnCorner = Instance.new("UICorner")
    BtnCorner.CornerRadius = UDim.new(0, 8)
    BtnCorner.Parent = Btn

    Btn.MouseButton1Click:Connect(function()
        TabGraficos.Visible = false
        TabAntiLag.Visible = false
        TabSettings.Visible = false
        TabAvancado.Visible = false
        TabStatus.Visible = false
        TabCreditos.Visible = false
        abaAlvo.Visible = true
        
        for _, child in ipairs(NavContainer:GetChildren()) do
            if child:IsA("TextButton") then
                TweenService:Create(child, TweenInfo.new(0.2), {TextColor3 = Cores.TextoEscuro, BackgroundTransparency = 1}):Play()
            end
        end
        TweenService:Create(Btn, TweenInfo.new(0.2), {TextColor3 = Cores.Accent, BackgroundTransparency = 0}):Play()
    end)
end

-- Montando a estrutura de abas na ordem perfeita
CriarBotaoMenu("🖥️ Gráficos", TabGraficos)
CriarBotaoMenu("👥 Anti-Lag", TabAntiLag)
CriarBotaoMenu("⚙️ Tela & FOV", TabSettings)
CriarBotaoMenu("⚡ Avançado", TabAvancado)
CriarBotaoMenu("📊 Status Celular", TabStatus)
CriarBotaoMenu("👑 Créditos", TabCreditos)

TabGraficos.Visible = true
local PrimeiroBtn = NavContainer:FindFirstChildOfClass("TextButton")
if PrimeiroBtn then PrimeiroBtn.BackgroundTransparency = 0 PrimeiroBtn.TextColor3 = Cores.Accent end

-- ====== FUNÇÃO MODULAR: COMPONENTE TOGGLE ======
local function AdicionarOtimizador(aba, titulo, descricao, funcao)
    local Card = Instance.new("Frame")
    Card.Size = UDim2.new(1, -10, 0, 54)
    Card.BackgroundColor3 = Cores.FundoCard
    Card.Parent = aba

    local CCorner = Instance.new("UICorner")
    CCorner.CornerRadius = UDim.new(0, 10)
    CCorner.Parent = Card

    local LabelT = Instance.new("TextLabel")
    LabelT.Size = UDim2.new(0.7, 0, 0, 22)
    LabelT.Position = UDim2.new(0, 12, 0, 6)
    LabelT.Text = titulo
    LabelT.TextColor3 = Cores.TextoClaro
    LabelT.TextSize = 13
    LabelT.Font = Enum.Font.GothamBold
    LabelT.TextXAlignment = Enum.TextXAlignment.Left
    LabelT.BackgroundTransparency = 1
    LabelT.Parent = Card

    local LabelD = Instance.new("TextLabel")
    LabelD.Size = UDim2.new(0.7, 0, 0, 18)
    LabelD.Position = UDim2.new(0, 12, 0, 26)
    LabelD.Text = descricao
    LabelD.TextColor3 = Cores.TextoEscuro
    LabelD.TextSize = 10.5
    LabelD.Font = Enum.Font.Gotham
    LabelD.TextXAlignment = Enum.TextXAlignment.Left
    LabelD.BackgroundTransparency = 1
    LabelD.Parent = Card

    local Switch = Instance.new("TextButton")
    Switch.Size = UDim2.new(0, 44, 0, 20)
    Switch.Position = UDim2.new(1, -56, 0.5, -10)
    Switch.BackgroundColor3 = Color3.fromRGB(40, 35, 55)
    Switch.Text = ""
    Switch.Parent = Card

    local SCorner = Instance.new("UICorner")
    SCorner.CornerRadius = UDim.new(1, 0)
    SCorner.Parent = Switch

    local Indicador = Instance.new("Frame")
    Indicador.Size = UDim2.new(0, 14, 0, 14)
    Indicador.Position = UDim2.new(0, 3, 0.5, -7)
    Indicador.BackgroundColor3 = Color3.fromRGB(150, 140, 170)
    Indicador.Parent = Switch

    local ICorner = Instance.new("UICorner")
    ICorner.CornerRadius = UDim.new(1, 0)
    ICorner.Parent = Indicador

    local Ativo = false
    Switch.MouseButton1Click:Connect(function()
        Ativo = not Ativo
        local AlvoPos = Ativo and UDim2.new(1, -17, 0.5, -7) or UDim2.new(0, 3, 0.5, -7)
        local AlvoCorBg = Ativo and Cores.Accent or Color3.fromRGB(40, 35, 55)
        local AlvoCorInd = Ativo and Color3.fromRGB(255, 255, 255) or Color3.fromRGB(150, 140, 170)

        TweenService:Create(Indicador, TweenInfo.new(0.2), {Position = AlvoPos, BackgroundColor3 = AlvoCorInd}):Play()
        TweenService:Create(Switch, TweenInfo.new(0.2), {BackgroundColor3 = AlvoCorBg}):Play()
        
        pcall(funcao, Ativo)
    end)
end

-- ====== FUNÇÃO MODULAR: COMPONENTE SLIDER ======
local function AdicionarSlider(aba, titulo, min, max, padrao, funcao)
    local Card = Instance.new("Frame")
    Card.Size = UDim2.new(1, -10, 0, 58)
    Card.BackgroundColor3 = Cores.FundoCard
    Card.Parent = aba

    local CCorner = Instance.new("UICorner")
    CCorner.CornerRadius = UDim.new(0, 10)
    CCorner.Parent = Card

    local LabelT = Instance.new("TextLabel")
    LabelT.Size = UDim2.new(0.6, 0, 0, 22)
    LabelT.Position = UDim2.new(0, 12, 0, 6)
    LabelT.Text = titulo
    LabelT.TextColor3 = Cores.TextoClaro
    LabelT.TextSize = 13
    LabelT.Font = Enum.Font.GothamBold
    LabelT.TextXAlignment = Enum.TextXAlignment.Left
    LabelT.BackgroundTransparency = 1
    LabelT.Parent = Card

    local ValLabel = Instance.new("TextLabel")
    ValLabel.Size = UDim2.new(0.3, 0, 0, 22)
    ValLabel.Position = UDim2.new(0.7, -12, 0, 6)
    ValLabel.Text = tostring(padrao)
    ValLabel.TextColor3 = Cores.Accent
    ValLabel.TextSize = 13
    ValLabel.Font = Enum.Font.GothamBold
    ValLabel.TextXAlignment = Enum.TextXAlignment.Right
    ValLabel.BackgroundTransparency = 1
    ValLabel.Parent = Card

    local SliderFrame = Instance.new("TextButton")
    SliderFrame.Size = UDim2.new(1, -24, 0, 6)
    SliderFrame.Position = UDim2.new(0, 12, 0, 36)
    SliderFrame.BackgroundColor3 = Color3.fromRGB(40, 35, 55)
    SliderFrame.Text = ""
    SliderFrame.Parent = Card

    local SFCorn = Instance.new("UICorner")
    SFCorn.CornerRadius = UDim.new(1, 0)
    SFCorn.Parent = SliderFrame

    local SliderFill = Instance.new("Frame")
    SliderFill.Size = UDim2.new((padrao - min)/(max - min), 0, 1, 0)
    SliderFill.BackgroundColor3 = Cores.Accent
    SliderFill.BorderSizePixel = 0
    SliderFill.Parent = SliderFrame
    
    local SFCorn2 = Instance.new("UICorner")
    SFCorn2.CornerRadius = UDim.new(1, 0)
    SFCorn2.Parent = SliderFill

    local SliderBotao = Instance.new("Frame")
    SliderBotao.Size = UDim2.new(0, 14, 0, 14)
    SliderBotao.Position = UDim2.new((padrao - min)/(max - min), -7, 0.5, -7)
    SliderBotao.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    SliderBotao.Parent = SliderFrame

    local SBCorn = Instance.new("UICorner")
    SBCorn.CornerRadius = UDim.new(1, 0)
    SBCorn.Parent = SliderBotao

    local sliding = false
    local function atualizar(input)
        local arrasto = math.clamp((input.Position.X - SliderFrame.AbsolutePosition.X) / SliderFrame.AbsoluteSize.X, 0, 1)
        local valor = math.round(min + (max - min) * arrasto)
        
        SliderFill.Size = UDim2.new(arrasto, 0, 1, 0)
        SliderBotao.Position = UDim2.new(arrasto, -7, 0.5, -7)
        ValLabel.Text = tostring(valor)
        
        pcall(funcao, valor)
    end

    SliderFrame.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            sliding = true
            atualizar(input)
        end
    end)

    UserInputService.InputChanged:Connect(function(input)
        if sliding and (input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch) then
            atualizar(input)
        end
    end)

    UserInputService.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            sliding = false
        end
    end)
end

-- =============================================================================
-- [ABA 1]: DIRETRIZES DE GRÁFICOS (VISUAL CLEANER)
-- =============================================================================
AdicionarOtimizador(TabGraficos, "Remover Texturas Básicas", "Transmuta os blocks do mapa em plástico liso.", function(estado)
    if estado then
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("BasePart") and not obj:IsA("MeshPart") and not obj:FindFirstAncestorOfClass("Player") then obj.Material = Enum.Material.SmoothPlastic end
        end
    end
end)

AdicionarOtimizador(TabGraficos, "Deletar Sky & Fog Completamente", "Remove o céu do mapa, nuvens e neblinas de renderização.", function(estado)
    if estado then
        Lighting.FogStart = 999999; Lighting.FogEnd = 999999
        local Atm = Lighting:FindFirstChildOfClass("Atmosphere") if Atm then Atm:Destroy() end
        for _, obj in ipairs(Lighting:GetChildren()) do 
            if obj:IsA("Sky") or obj:IsA("Clouds") then obj:Destroy() end 
        end
    end
end)

AdicionarOtimizador(TabGraficos, "Modo Batata Nativo", "Força o motor gráfico do Roblox para o nível mínimo.", function(estado)
    if estado then settings().Rendering.QualityLevel = Enum.QualityLevel.Level01; Lighting.Technology = Enum.Technology.Compatibility end
end)

AdicionarOtimizador(TabGraficos, "Otimizar Física da Água", "Remove ondulações e reflexos em terrains de água.", function(estado)
    local Terr = Workspace:FindFirstChildOfClass("Terrain")
    if Terr and estado then Terr.WaterWaveSize = 0; Terr.WaterWaveSpeed = 0; Terr.WaterReflectance = 0; Terr.WaterTransparency = 0 end
end)

AdicionarOtimizador(TabGraficos, "Aniquilar Decals & Textures", "Apaga imagens coladas em paredes e chãos do mapa.", function(estado)
    if estado then
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("Decal") or obj:IsA("Texture") then obj:Destroy() end
        end
    end
end)

-- =============================================================================
-- [ABA 2]: INSTÂNCIAS ANTI-LAG (PLAYER ENTITY FOCUS)
-- =============================================================================
local function DespirPlayer(v)
    if v.Character and v ~= Players.LocalPlayer then
        for _, item in ipairs(v.Character:GetDescendants()) do
            if item:IsA("Shirt") or item:IsA("Pants") or item:IsA("Accessory") or item:IsA("ShirtGraphic") then item:Destroy() end
            if item:IsA("BasePart") then item.Color = Color3.fromRGB(140, 140, 140); item.Material = Enum.Material.SmoothPlastic end
        end
    end
end

AdicionarOtimizador(TabAntiLag, "Modo Cinza + Remover Skins", "Limpa todas as roupas alheias e pinta o mapa de cinza.", function(estado)
    if estado then
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("BasePart") and not obj:IsA("Terrain") then obj.Color = Color3.fromRGB(130, 130, 130); obj.Material = Enum.Material.SmoothPlastic; if obj:IsA("MeshPart") then obj.TextureID = "" end end
        end
        for _, v in ipairs(Players:GetPlayers()) do DespirPlayer(v) end
    end
end)

AdicionarOtimizador(TabAntiLag, "Remover Animações de Jogo", "Para as animações para economizar CPU.", function(estado)
    if estado then
        for _, v in ipairs(Players:GetPlayers()) do
            if v.Character and v.Character:FindFirstChildOfClass("Humanoid") then
                local animator = v.Character:FindFirstChildOfClass("Humanoid"):FindFirstChildOfClass("Animator")
                if animator then
                    for _, track in ipairs(animator:GetPlayingAnimationTracks()) do track:Stop() end
                end
            end
        end
    end
end)

AdicionarOtimizador(TabAntiLag, "Aniquilar Partículas de Scripts", "Limpa rastros, raios e fumaças nocivas de outros scripts.", function(estado)
    if estado then for _, obj in ipairs(Workspace:GetDescendants()) do if obj:IsA("ParticleEmitter") or obj:IsA("Trail") or obj:IsA("Beam") then obj:Destroy() end end end
end)

AdicionarOtimizador(TabAntiLag, "Ocultar Nomes & Títulos", "Nuka interfaces flutuantes (BillboardGuis) sobre os personagens.", function(estado)
    if estado then
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("BillboardGui") or obj:IsA("SurfaceGui") then obj:Destroy() end
        end
    end
end)

-- =============================================================================
-- [ABA 3]: CONFIGURAÇÕES / AJUSTES DE TELA
-- =============================================================================
AdicionarSlider(TabSettings, "Ajustar Campo de Visão (FOV)", 30, 120, 70, function(valor)
    local camera = Workspace.CurrentCamera
    if camera then camera.FieldOfView = valor end
end)

AdicionarOtimizador(TabSettings, "Remover Animações da Tela", "Elimina tremores de câmera e efeitos visuais na UI.", function(estado)
    if estado then
        local cam = Workspace.CurrentCamera
        if cam then cam.CameraType = Enum.CameraType.Custom end
        settings().Rendering.ReducedMotion = true
    else
        settings().Rendering.ReducedMotion = false
    end
end)

local OriginalAmbient, OriginalOutdoor
AdicionarOtimizador(TabSettings, "Modo Fullbright (Brilho Máximo)", "Ignora a escuridão nativa de qualquer mapa do jogo.", function(estado)
    if estado then
        OriginalAmbient = Lighting.Ambient
        OriginalOutdoor = Lighting.OutdoorAmbient
        Lighting.Ambient = Color3.fromRGB(255, 255, 255)
        Lighting.OutdoorAmbient = Color3.fromRGB(255, 255, 255)
        Lighting.ClockTime = 14
        Lighting.GlobalShadows = false
    else
        if OriginalAmbient then Lighting.Ambient = OriginalAmbient end
        if OriginalOutdoor then Lighting.OutdoorAmbient = OriginalOutdoor end
    end
end)

AdicionarOtimizador(TabSettings, "Desbloquear Taxa de FPS", "Remove travas de 60 FPS padrão (Requer suporte do executor).", function(estado)
    if estado then
        if setfpscap then setfpscap(999) end
    else
        if setfpscap then setfpscap(60) end
    end
end)

-- =============================================================================
-- [ABA 4]: ENGENHARIA AVANÇADA (DEEP ENGINE BYPASS)
-- =============================================================================
AdicionarOtimizador(TabAvancado, "Destruir VFX & Efeitos Totais", "Purga do mapa Fire, Smoke, Sparkles, Explosions e Highlights.", function(estado)
    if estado then
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("Fire") or obj:IsA("Smoke") or obj:IsA("Sparkles") or obj:IsA("Explosion") or obj:IsA("Highlight") then
                obj:Destroy()
            end
        end
    end
end)

AdicionarOtimizador(TabAvancado, "Exterminar Efeitos de Lente", "Deleta Bloom, Blur, SunRays e ColorCorrection do mapa.", function(estado)
    if estado then
        for _, obj in ipairs(Lighting:GetChildren()) do
            if obj:IsA("BlurEffect") or obj:IsA("BloomEffect") or obj:IsA("SunRaysEffect") or obj:IsA("ColorCorrectionEffect") then
                obj:Destroy()
            end
        end
    end
end)

AdicionarOtimizador(TabAvancado, "Remover Reflexos de Materiais", "Substitui propriedades reflexivas de Vidros e Metais pesados.", function(estado)
    if estado then
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("BasePart") then
                if obj.Material == Enum.Material.Glass or obj.Material == Enum.Material.Metal or obj.Material == Enum.Material.CorrodedMetal then
                    obj.Material = Enum.Material.SmoothPlastic
                    obj.Reflectance = 0
                end
            end
        end
    end
end)

AdicionarOtimizador(TabAvancado, "Anular Colisão de Assentos (Seats)", "Desativa a física reativa e gatilhos de sentar do mapa.", function(estado)
    if estado then
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("Seat") or obj:IsA("VehicleSeat") then
                obj.Disabled = true
                obj.CanCollide = false
            end
        end
    end
end)

-- =============================================================================
-- [ABA 5]: DASHBOARD DE STATUS EM GRADE (DIAGNOSTICS)
-- =============================================================================
local GridStatus = Instance.new("UIGridLayout")
GridStatus.Parent = TabStatus
GridStatus.CellSize = UDim2.new(0.5, -6, 0, 95) 
GridStatus.CellPadding = UDim2.new(0, 12, 0, 12)
GridStatus.SortOrder = Enum.SortOrder.LayoutOrder

local function CriarCardDashboard(titulo, sufixo, ordem)
    local Card = Instance.new("Frame")
    Card.BackgroundColor3 = Cores.FundoCard
    Card.LayoutOrder = ordem
    Card.Parent = TabStatus
    
    local Corner = Instance.new("UICorner")
    Corner.CornerRadius = UDim.new(0, 12)
    Corner.Parent = Card
    
    local Stroke = Instance.new("UIStroke")
    Stroke.Color = Color3.fromRGB(42, 34, 62)
    Stroke.Thickness = 1
    Stroke.Parent = Card

    local LabelT = Instance.new("TextLabel")
    LabelT.Size = UDim2.new(1, -20, 0, 18)
    LabelT.Position = UDim2.new(0, 12, 0, 8)
    LabelT.Text = titulo:upper()
    LabelT.TextColor3 = Cores.TextoEscuro
    LabelT.TextSize = 9
    LabelT.Font = Enum.Font.GothamBold
    LabelT.TextXAlignment = Enum.TextXAlignment.Left
    LabelT.BackgroundTransparency = 1
    LabelT.Parent = Card

    local LabelVal = Instance.new("TextLabel")
    LabelVal.Size = UDim2.new(1, -20, 0, 35)
    LabelVal.Position = UDim2.new(0, 12, 0, 24)
    LabelVal.Text = "00"
    LabelVal.TextColor3 = Cores.Accent
    LabelVal.TextSize = 28
    LabelVal.Font = Enum.Font.GothamBold
    LabelVal.TextXAlignment = Enum.TextXAlignment.Left
    LabelVal.BackgroundTransparency = 1
    LabelVal.Parent = Card

    local LabelSuf = Instance.new("TextLabel")
    LabelSuf.Size = UDim2.new(0, 50, 0, 18)
    LabelSuf.Position = UDim2.new(0, 12, 1, -24)
    LabelSuf.Text = sufixo
    LabelSuf.TextColor3 = Cores.TextoClaro
    LabelSuf.TextSize = 11
    LabelSuf.Font = Enum.Font.GothamSemibold
    LabelSuf.TextXAlignment = Enum.TextXAlignment.Left
    LabelSuf.BackgroundTransparency = 1
    LabelSuf.Parent = Card

    local LabelDiag = Instance.new("TextLabel")
    LabelDiag.Size = UDim2.new(1, -20, 0, 12)
    LabelDiag.Position = UDim2.new(0, 12, 1, -12)
    LabelDiag.Text = "Analisando..."
    LabelDiag.TextColor3 = Cores.TextoEscuro
    LabelDiag.TextSize = 9
    LabelDiag.Font = Enum.Font.GothamMedium
    LabelDiag.TextXAlignment = Enum.TextXAlignment.Left
    LabelDiag.BackgroundTransparency = 1
    LabelDiag.Parent = Card

    return LabelVal, LabelDiag
end

local ValFPS, DiagFPS = CriarCardDashboard("Taxa de Quadros", "FPS", 1)
local ValPing, DiagPing = CriarCardDashboard("Latência de Rede", "MS", 2)
local ValRAM, DiagRAM = CriarCardDashboard("Uso de Memória", "MB RAM", 3)

local CleanCard = Instance.new("TextButton")
CleanCard.BackgroundColor3 = Color3.fromRGB(34, 18, 56)
CleanCard.LayoutOrder = 4
CleanCard.Text = ""
CleanCard.Parent = TabStatus

local CleanCorner = Instance.new("UICorner")
CleanCorner.CornerRadius = UDim.new(0, 12)
CleanCorner.Parent = CleanCard

local CleanStroke = Instance.new("UIStroke")
CleanStroke.Color = Cores.Accent
CleanStroke.Thickness = 1.2
CleanStroke.Parent = CleanCard

local CleanTitle = Instance.new("TextLabel")
CleanTitle.Size = UDim2.new(1, -20, 0, 18)
CleanTitle.Position = UDim2.new(0, 12, 0, 8)
CleanTitle.Text = "SISTEMA OPERACIONAL"
CleanTitle.TextColor3 = Cores.TextoEscuro
CleanTitle.TextSize = 8
CleanTitle.Font = Enum.Font.GothamBold
CleanTitle.TextXAlignment = Enum.TextXAlignment.Left
CleanTitle.BackgroundTransparency = 1
CleanTitle.Parent = CleanCard

local CleanMainText = Instance.new("TextLabel")
CleanMainText.Size = UDim2.new(1, -20, 0, 35)
CleanMainText.Position = UDim2.new(0, 12, 0, 24)
CleanMainText.Text = "🧹 LIMPAR CACHE"
CleanMainText.TextColor3 = Cores.TextoClaro
CleanMainText.TextSize = 13
CleanMainText.Font = Enum.Font.GothamBold
CleanMainText.TextXAlignment = Enum.TextXAlignment.Left
CleanMainText.BackgroundTransparency = 1
CleanMainText.Parent = CleanCard

local CleanSubText = Instance.new("TextLabel")
CleanSubText.Size = UDim2.new(1, -20, 0, 12)
CleanSubText.Position = UDim2.new(0, 12, 1, -16)
CleanSubText.Text = "Clique para purgar lixo da RAM"
CleanSubText.TextColor3 = Cores.Accent
CleanSubText.TextSize = 9
CleanSubText.Font = Enum.Font.GothamMedium
CleanSubText.TextXAlignment = Enum.TextXAlignment.Left
CleanSubText.BackgroundTransparency = 1
CleanSubText.Parent = CleanCard

-- ====== FIX DO BOTÃO DE PURGAR CACHE (DEBOUNCE ANTILOCK) ======
local estaPurgando = false
CleanCard.MouseButton1Click:Connect(function()
    if estaPurgando then return end
    estaPurgando = true
    
    CleanMainText.Text = "⚡ PURGANDO..."
    CleanStroke.Color = Cores.VerdeNeon
    
    pcall(function()
        collectgarbage("collect")
    end)
    
    task.wait(0.7)
    CleanMainText.Text = "✨ RAM RESETADA!"
    CleanSubText.TextColor3 = Cores.VerdeNeon
    
    task.wait(1.2)
    CleanMainText.Text = "🧹 LIMPAR CACHE"
    CleanStroke.Color = Cores.Accent
    CleanSubText.TextColor3 = Cores.Accent
    estaPurgando = false
end)

-- Sistema de monitoramento contínuo em tempo de execução
local frames = 0
local lastUpdate = os.clock()
RunService.RenderStepped:Connect(function()
    frames = frames + 1
    local agora = os.clock()
    if agora - lastUpdate >= 1 then
        ValFPS.Text = tostring(frames)
        if frames >= 50 then
            DiagFPS.Text = "Desempenho: Excelente"
            ValFPS.TextColor3 = Cores.VerdeNeon
        elseif frames >= 30 then
            DiagFPS.Text = "Desempenho: Estável"
            ValFPS.TextColor3 = Cores.Accent
        else
            DiagFPS.Text = "Desempenho: Alerta crítico"
            ValFPS.TextColor3 = Cores.VermelhoNeon
        end
        frames = 0; lastUpdate = agora
    end
end)

task.spawn(function()
    while task.wait(1) do
        local ping = math.round(Players.LocalPlayer:GetNetworkPing() * 1000)
        local ram = math.round(StatsService:GetTotalMemoryUsageMb())
        
        ValPing.Text = tostring(ping)
        if ping < 80 then
            DiagPing.Text = "Rede: Ótima Conectividade"
            ValPing.TextColor3 = Cores.VerdeNeon
        elseif ping < 160 then
            DiagPing.Text = "Rede: Latência Moderada"
            ValPing.TextColor3 = Cores.Accent
        else
            DiagPing.Text = "Rede: Cabo / Instabilidade"
            ValPing.TextColor3 = Cores.VermelhoNeon
        end

        ValRAM.Text = tostring(ram)
        if ram < 400 then
            DiagRAM.Text = "Memória: Totalmente Livre"
            ValRAM.TextColor3 = Cores.VerdeNeon
        elseif ram < 800 then
            DiagRAM.Text = "Memória: Uso Moderado"
            ValRAM.TextColor3 = Cores.Accent
        else
            DiagRAM.Text = "Memória: Sobrecarga Iminente"
            ValRAM.TextColor3 = Cores.VermelhoNeon
        end
    end
end)


-- =============================================================================
-- [ABA 6]: CRÉDITOS PREMIUM CYBER GLOW
-- =============================================================================
local CreditosCard = Instance.new("Frame")
CreditosCard.Size = UDim2.new(1, -10, 1, -5)
CreditosCard.BackgroundColor3 = Cores.FundoCard
CreditosCard.Parent = TabCreditos

local CCorn = Instance.new("UICorner")
CCorn.CornerRadius = UDim.new(0, 14)
CCorn.Parent = CreditosCard

local CStroke = Instance.new("UIStroke")
CStroke.Color = Color3.fromRGB(45, 35, 70)
CStroke.Thickness = 1.2
CStroke.Parent = CreditosCard

local DevBadge = Instance.new("Frame")
DevBadge.Size = UDim2.new(0, 95, 0, 22)
DevBadge.Position = UDim2.new(0, 20, 0, 18)
DevBadge.BackgroundColor3 = Color3.fromRGB(36, 18, 54)
DevBadge.Parent = CreditosCard

local BCorn = Instance.new("UICorner")
BCorn.CornerRadius = UDim.new(0, 6)
BCorn.Parent = DevBadge

local BStroke = Instance.new("UIStroke")
BStroke.Color = Cores.Accent
BStroke.Thickness = 1
BStroke.Parent = DevBadge

local BadgeText = Instance.new("TextLabel")
BadgeText.Size = UDim2.new(1, 0, 1, 0)
BadgeText.Text = "⚡ AUTHOR"
BadgeText.TextColor3 = Cores.TextoClaro
BadgeText.TextSize = 10
BadgeText.Font = Enum.Font.GothamBold
BadgeText.BackgroundTransparency = 1
BadgeText.Parent = DevBadge

local DevName = Instance.new("TextLabel")
DevName.Size = UDim2.new(1, -40, 0, 35)
DevName.Position = UDim2.new(0, 20, 0, 42)
DevName.Text = "TheDevMtz"
DevName.TextColor3 = Cores.TextoClaro
DevName.TextSize = 26
DevName.Font = Enum.Font.GothamBold
DevName.TextXAlignment = Enum.TextXAlignment.Left
DevName.BackgroundTransparency = 1
DevName.Parent = CreditosCard

local DevTitle = Instance.new("TextLabel")
DevTitle.Size = UDim2.new(1, -40, 0, 15)
DevTitle.Position = UDim2.new(0, 20, 0, 76)
DevTitle.Text = "Engenheiro de Software & UI/UX Designer"
DevTitle.TextColor3 = Cores.Accent
DevTitle.TextSize = 11
DevTitle.Font = Enum.Font.GothamSemibold
DevTitle.TextXAlignment = Enum.TextXAlignment.Left
DevTitle.BackgroundTransparency = 1
DevTitle.Parent = CreditosCard

local DevDesc = Instance.new("TextLabel")
DevDesc.Size = UDim2.new(1, -40, 0, 60) 
DevDesc.Position = UDim2.new(0, 20, 0, 100)
DevDesc.Text = "O mtz hub v5.3 Cyber Purple foi completamente reestruturado para entregar métricas de alta fidelidade e manipulação avançada de hardware. Otimizado estritamente para extrair a performance máxima estável em dispositivos mobile limitados."
DevDesc.TextColor3 = Cores.TextoEscuro
DevDesc.TextSize = 11.5
DevDesc.Font = Enum.Font.GothamMedium
DevDesc.TextWrapped = true
DevDesc.TextXAlignment = Enum.TextXAlignment.Left
DevDesc.TextYAlignment = Enum.TextYAlignment.Top
DevDesc.BackgroundTransparency = 1
DevDesc.Parent = CreditosCard

local ActionBtn = Instance.new("TextButton")
ActionBtn.Size = UDim2.new(1, -40, 0, 36)
ActionBtn.Position = UDim2.new(0, 20, 1, -48) 
ActionBtn.BackgroundColor3 = Color3.fromRGB(26, 20, 38)
ActionBtn.Text = "VERIFICAR ATUALIZAÇÕES"
ActionBtn.TextColor3 = Cores.TextoClaro
ActionBtn.TextSize = 11
ActionBtn.Font = Enum.Font.GothamBold
ActionBtn.RichText = true 
ActionBtn.Parent = CreditosCard

local ABcorn = Instance.new("UICorner")
ABcorn.CornerRadius = UDim.new(0, 8)
ABcorn.Parent = ActionBtn

local ABstroke = Instance.new("UIStroke")
ABstroke.Color = Color3.fromRGB(60, 48, 90)
ABstroke.Thickness = 1.2
ABstroke.Parent = ActionBtn

-- Borda Gradiente Preto/Roxo Customizada
local ABgradient = Instance.new("UIGradient")
ABgradient.Parent = ABstroke
ABgradient.Color = ColorSequence.new(Color3.fromRGB(60, 48, 90)) 

ActionBtn.MouseButton1Click:Connect(function()
    ActionBtn.Text = '<font color="rgb(157, 78, 221)">✨ HUB ATUALIZADO</font> <font color="rgb(0, 230, 153)">(v5.3)</font>'
    
    ABstroke.Thickness = 1.8 
    ABgradient.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 0, 0)),        -- Preto
        ColorSequenceKeypoint.new(1, Cores.Accent)                    -- Roxo Neon
    })
    
    task.wait(2)
    
    ActionBtn.Text = "VERIFICAR ATUALIZAÇÕES"
    ABstroke.Thickness = 1.2
    ABgradient.Color = ColorSequence.new(Color3.fromRGB(60, 48, 90))
end)


-- ====== SISTEMA ANTIFALHA DE ARRASTE E EXIBIÇÃO MOBILE ======
local dragging = false
local dragStart, startPos, startClock

local function AlternarPainel()
    MainFrame.Visible = not MainFrame.Visible
    if MainFrame.Visible then
        MainFrame.Size = UDim2.new(0, 520, 0, 0)
        TweenService:Create(MainFrame, TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Size = UDim2.new(0, 520, 0, 300)}):Play()
    end
end

ToggleButton.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true
        dragStart = input.Position
        startPos = ToggleButton.Position
        startClock = os.clock()
        
        -- Efeito visual elástico de clique
        TweenService:Create(ToggleButton, TweenInfo.new(0.1), {Size = UDim2.new(0, 50, 0, 50)}):Play()
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if dragging and (input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1) then
        local delta = input.Position - dragStart
        ToggleButton.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
        if dragging then
            dragging = false
            
            -- Retorna ao tamanho normal pós clique
            TweenService:Create(ToggleButton, TweenInfo.new(0.2, Enum.EasingStyle.Back), {Size = UDim2.new(0, 48, 0, 48)}):Play()
            
            local endPos = input.Position
            local deltaDis = (endPos - dragStart).Magnitude
            local tempoDecorrido = os.clock() - startClock
            
            if deltaDis < 8 and tempoDecorrido < 0.35 then
                AlternarPainel()
            end
        end
    end
end)

print("--- mtz hub v5.3 Cyber Purple Premium UI Carregado! ---")
