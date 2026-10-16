-- =============================================
-- 🤖 M7 | تفريم + ضغط كلمات تلقائي (زر واحد) v39 + نظام المفاتيح + Anti-AFK
-- v30:
--   * تجميد حركة اللاعب طول ما زر التفريم شغال (ويرجع الحركة أول ما تطفيه)
--   * إصلاح غسيل الفلوس: إشعار "تم شراء أداة اختراق مقابل 800" كان يتحسب كإشعار غسيل (فيه كلمة "مقابل")،
--     الحين نتجاهل أي إشعار فيه "أداة" أو "اختراق"
--   * أقصى وقت انتظار عند برومبت الغسيل = 10 ثواني
--   * الغسيل: أول مرة بعد ما يخلص جولة الأربع صرافات (سواء سرق منها أو لا)،
--     وبعدها يغسل علطول بعد كل صرافة ينجح بسرقتها
-- v31: بعد الغسيل ينتقل لمكان شراء الأداة ويشتريها، وبعدها ينتظر صرافة تنفك
-- v32:
--   * أثناء غسيل الفلوس تنقفل حزمة شراء أداة الاختراق (ما يشتري أبداً وقت الغسيل)
--   * بعد ما يخلص الغسيل: ينتقل لمكان شراء الأداة، يرجّع حزمة الشراء، يشتري الأداة،
--     وبعدها يروح مكان الانتظار
-- v34:
--   * زر جديد تحت بدأ التفريم: "تغيير السيرفر تلقائيا و بدأ التفريم" (وصفه تحته)
--     يغير السيرفر لأقل سيرفر فيه لاعبين (مرتّب، مو عشوائي) بس وهو بمكان الانتظار ولا فيه صرافة جاهزة
--   * حفظ حالة الأزرار: بعد الدخول للسيرفر الجديد يشتغل التفريم تلقائي (ويأكد المفتاح المحفوظ)
-- v33:
--   * قفل على مستوى الريموت: أي حزمة فيها "buy" تنحجب وقت الغسيل (حتى لو من سكربتات اللعبة) ويطبع مصدرها
--   * وقت الغسيل يعطّل أي برومبت ثاني قريب غير برومبت الغسيل، ويرجّعها بعده
--   * إحداثيات شراء مستقلة (POS_BUY) والشراء ما يصير إلا وهو قريب منها (BUY_RANGE)
-- v35:
--   * الغسيل: يوقف الضغط أول ما ينتأكد، ويعطّل البرومبت، وما يضغط أي برومبت نصه شراء أداة
--   * البرومبتات المعطّلة ما ترجع إلا بعد ما يبتعد عن مكان الغسيل
--   * وضع تغيير السيرفر: ما يشتري الأداة بعد الغسيل (يشتريها قبل الصراف بالسيرفر الجديد)
--   * وضع تغيير السيرفر + مفتاح محفوظ صحيح: يتخطى قائمة المفتاح بدون صوت ولا إشعار ولا واجهة
--   * تغيير السيرفر يفضّل السيرفرات الفاضية أكثر (0 لاعبين، ٥ صفحات، لين ١٥ محاولة)
-- v36:
--   * إعادة ضبط حالة الصرافات (closed/block) عند الدخول لسيرفر جديد (مؤقتات السيرفر القديم كانت تخليه ينتظر)
--   * قفل الريموت ينعاد تركيبه بكل سيرفر جديد (مربوط بـ JobId)
--   * الغسيل: إيقاف الضغط فوراً (حتى الضغطات المعلّقة) أول ما ينتأكد
--   * لو انقطع وسط الغسيل (تغيير سيرفر / إعادة تشغيل) يكمل الغسيل أول شي
--   * وضع تغيير السيرفر: يتجاهل أي صرافة ترسبنت، والوصف "تغيير السيرفر..." ثابت مع النقاط
-- v37:
--   * وضع تغيير السيرفر صار يمشي على نفس نظام الغسيل حق زر "بدأ التفريم" بالضبط
--   * تغيير السيرفر: يرتّب من الأقل لاعبين، يتجاهل آخر ١٢ سيرفر، يجرب لين ٣٠ سيرفر
-- v38:
--   * وضع تغيير السيرفر: بعد الغسيل ما يشتري الأداة أبداً، يروح مكان الانتظار ويغير السيرفر علطول
--     (الأداة تنشترى بالسيرفر الجديد قبل أول صراف)
--   * اختيار السيرفر: يفلتر على أقصى عدد لاعبين (HOP_MAX_PLAYERS) ويختار عشوائي من أقل ٥ سيرفرات
--     (عشان ما يتزاحم الكل على نفس السيرفر)، ولو دخل سيرفر مزدحم يغيّر علطول بدون تفريم
--   * يفرّق بين تغيير السيرفر من السكربت (يشتغل علطول بدون مفتاح) وبين دخولك للماب بنفسك
--     (يطلع لك قائمة المفاتيح ويطفي الحفظ التلقائي)
-- v39: (إصلاح: الغسيل ما يضغط شي بعد تغيير السيرفر)
--   * السبب الأساسي: السكربت نفسه كان يعطّل برومبت الغسيل (disableOthers) لو نصه ما انقرأ أول ما دخل السيرفر الجديد
--     الحين ما يعطّل إلا البرومبتات اللي نصها شراء أداة فعلاً، وكل محاولة تبدأ برجوع أي برومبت معطّل
--   * البحث بالاسم (StartProximity) ما يختار برومبت نصه شراء أداة (نفس المكان)
--   * لو ما لقى برومبت بالنص/الاسم يجرب أي برومبت قريب من مكان الغسيل مو نصه شراء
--   * لو البرومبت المختار صار نصه شراء أثناء الغسيل يدور على برومبت غسيل ثاني بدل ما يوقف
--   * لو سرق فلوس وما لقى برومبت ما يحكم "ما فيه فلوس" من أول مرة، يعيد المحاولة
--   * يطبع بالكونسل كل البرومبتات القريبة (الاسم/النص/مفعّل) لو ما لقى برومبت، عشان نعرف المشكلة بالضبط
-- =============================================

local Players       = game:GetService("Players")
local RunService    = game:GetService("RunService")
local UIS           = game:GetService("UserInputService")
local TweenService  = game:GetService("TweenService")
local GuiService    = game:GetService("GuiService")
local RS            = game:GetService("ReplicatedStorage")
local player        = Players.LocalPlayer

if not game:IsLoaded() then game.Loaded:Wait() end

local ENV = (getgenv and getgenv()) or _G

-- =============================================
-- تغيير السيرفر + حفظ الإعدادات (HOP)
-- set.farm = زر بدأ التفريم شغال | set.hop = وضع تغيير السيرفر شغال
-- set.seen = آخر السيرفرات اللي دخلها (عشان ما يرجع لها)
-- set.hopJob = السيرفر اللي السكربت قاصده (يعرف فيه إنه دخل بتغيير السيرفر مو يدوي)
-- =============================================
local HOP = {
    on = false, busy = false, lastTry = -100, queued = false,
    arrived = false, crowded = false, expect = 0,
    set = {farm = false, hop = false, seen = {}},
    path = "M7_FakAlfasla_Settings.json",
    http = game:GetService("HttpService"),
    tp = game:GetService("TeleportService"),
}

function HOP.load()
    pcall(function()
        if isfile and isfile(HOP.path) then
            local d = HOP.http:JSONDecode(readfile(HOP.path))
            if type(d) == "table" then
                HOP.set.farm = d.farm == true
                HOP.set.hop = d.hop == true
                HOP.set.seen = (type(d.seen) == "table") and d.seen or {}
                HOP.set.hopJob = (type(d.hopJob) == "string") and d.hopJob or nil
                HOP.set.hopAt = tonumber(d.hopAt) or 0
                HOP.set.expect = tonumber(d.expect) or 0
            end
        end
    end)
end

function HOP.save()
    pcall(function()
        if writefile then writefile(HOP.path, HOP.http:JSONEncode(HOP.set)) end
    end)
end

HOP.load()

-- هل دخل هذا السيرفر بتغيير السيرفر من السكربت؟ (أو دخلته انت بنفسك؟)
do
    local td = nil
    pcall(function() td = HOP.tp:GetLocalPlayerTeleportData() end)
    if type(td) == "table" and td.m7hop == true then HOP.arrived = true end
    if HOP.set.hopJob and HOP.set.hopJob == game.JobId
        and os.time() - (HOP.set.hopAt or 0) < 300 then
        HOP.arrived = true
    end
    HOP.expect = tonumber(HOP.set.expect) or 0
    HOP.set.hopJob = nil
    if not HOP.arrived then
        -- دخول يدوي: ما يشتغل تلقائي، ويطلع قائمة المفاتيح
        HOP.set.farm = false
        HOP.set.hop = false
    end
    HOP.save()
end

-- يسجّل السيرفر الحالي ضمن آخر السيرفرات اللي دخلها
do
    local s, found = HOP.set.seen, false
    for _, id in ipairs(s) do if id == game.JobId then found = true end end
    if not found then s[#s + 1] = game.JobId end
    while #s > 12 do table.remove(s, 1) end
    HOP.save()
end

for _, k in ipairs({"M7_FarmCleanup", "M7_WordsCleanup", "M7_AllCleanup"}) do
    if ENV[k] then pcall(ENV[k]) end
end

-- =============================================
-- أرقام عربية
-- =============================================
local AR_DIGITS = {["0"]="٠", ["1"]="١", ["2"]="٢", ["3"]="٣", ["4"]="٤",
                   ["5"]="٥", ["6"]="٦", ["7"]="٧", ["8"]="٨", ["9"]="٩"}
local function toArabic(n)
    return (string.gsub(tostring(n), "%d", AR_DIGITS))
end

-- =============================================
-- 🔑 نظام المفاتيح
-- =============================================
local Stunts = {notify = function() end}
local keyOk = false
do
    local KEY_TITLE     = "تفريم | M7"
    local VALID_KEYS = {
        "حمد@KS2847xQpLmNv91",
        "محمد@KS7391zRdWqYjB84",
    }
    local KEY_SAVE_PATH = "M7_FakAlfasla_Key.txt"
    local KEY_G_NAME    = "M7_FakAlfasla_SavedKey_" .. tostring(player.UserId)
    local GLOW_SPEED    = 2.0

    if ENV.M7_KeyAbort then pcall(ENV.M7_KeyAbort) end

    local gate = {done = false, ok = false}
    local keyVerified = false

    local keyGui = Instance.new("ScreenGui")
    keyGui.Name           = "M7_FaslaKeyGui"
    keyGui.ResetOnSpawn   = false
    keyGui.IgnoreGuiInset = true
    keyGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    local okParent = pcall(function() keyGui.Parent = game:GetService("CoreGui") end)
    if not okParent then keyGui.Parent = player:WaitForChild("PlayerGui") end

    local clickSound = Instance.new("Sound")
    clickSound.SoundId = "rbxassetid://6895079853"
    clickSound.Volume  = 0.7
    clickSound.Parent  = keyGui
    keyGui.DisplayOrder = 10

    local notifSound = Instance.new("Sound")
    notifSound.SoundId = "rbxassetid://6542152011"
    notifSound.Volume  = 1.5
    notifSound.Parent  = keyGui

    local clickDebounce = false
    local function playClick()
        if clickDebounce then return end
        clickDebounce = true
        clickSound:Play()
        task.delay(0.08, function() clickDebounce = false end)
    end

    local function applyNotifTextGlow(label, color1, color2)
        task.spawn(function()
            while label and label.Parent do
                TweenService:Create(label, TweenInfo.new(1.5), {TextColor3 = color1}):Play()
                task.wait(1.5)
                TweenService:Create(label, TweenInfo.new(1.5), {TextColor3 = color2}):Play()
                task.wait(1.5)
            end
        end)
    end

    local function applyNotifGoldStroke(object)
        local st = object:FindFirstChildOfClass("UIStroke") or Instance.new("UIStroke", object)
        st.Thickness       = 2
        st.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
        task.spawn(function()
            while st and st.Parent do
                TweenService:Create(st, TweenInfo.new(1.5), {Color = Color3.fromRGB(255, 215, 0)}):Play()
                task.wait(1.5)
                TweenService:Create(st, TweenInfo.new(1.5), {Color = Color3.fromRGB(255, 140, 0)}):Play()
                task.wait(1.5)
            end
        end)
    end

    local function sendNotification(text, duration)
        local isLong = (utf8.len(text) or #text) > 45
        local notifW = 0.25
        local notifH = 0.14
        local nf = Instance.new("Frame", keyGui)
        nf.Size                   = UDim2.new(notifW, 0, notifH, 0)
        nf.Position               = UDim2.new(1.2, 0, 0.45, 0)
        nf.BorderSizePixel        = 0
        nf.BackgroundTransparency = 1
        Instance.new("UICorner", nf)
        local ng = Instance.new("UIGradient", nf)
        ng.Color = ColorSequence.new({
            ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 20, 50)),
            ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 150, 255))
        })
        applyNotifGoldStroke(nf)
        notifSound:Play()
        TweenService:Create(nf, TweenInfo.new(0.3), {BackgroundTransparency = 0}):Play()
        local msg = Instance.new("TextLabel", nf)
        msg.Size               = UDim2.new(0.82, 0, 0.4, 0)
        msg.Position           = UDim2.new(0.05, 0, 0.15, 0)
        msg.Text               = text
        msg.Font               = Enum.Font.GothamBold
        msg.TextScaled         = true
        msg.TextWrapped        = not isLong
        msg.TextColor3         = Color3.new(1, 1, 1)
        msg.BackgroundTransparency = 1
        local byl = Instance.new("TextLabel", nf)
        byl.Size               = UDim2.new(1, 0, 0.2, 0)
        byl.Position           = UDim2.new(0, 0, 0.65, 0)
        byl.Text               = "By M7"
        byl.Font               = Enum.Font.Michroma
        byl.TextScaled         = true
        byl.BackgroundTransparency = 1
        applyNotifTextGlow(byl, Color3.fromRGB(255, 215, 0), Color3.fromRGB(255, 140, 0))
        local closeX = Instance.new("TextButton", nf)
        closeX.Size                   = UDim2.new(0, 11, 0, 11)
        closeX.Position               = UDim2.new(1, -13, 0, 3)
        closeX.BackgroundTransparency = 1
        closeX.Text                   = "X"
        closeX.TextColor3             = Color3.fromRGB(180, 180, 180)
        closeX.TextScaled             = true
        closeX.Font                   = Enum.Font.Michroma
        closeX.ZIndex                 = 10
        closeX.BorderSizePixel        = 0
        local function dismissNotif()
            TweenService:Create(nf, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {BackgroundTransparency = 1}):Play()
            nf:TweenPosition(UDim2.new(1.2, 0, 0.45, 0), "In", "Quad", 0.4, true)
            task.delay(0.4, function() if nf and nf.Parent then nf:Destroy() end end)
        end
        closeX.MouseButton1Click:Connect(dismissNotif)
        nf:TweenPosition(UDim2.new(1 - notifW - 0.01, 0, 0.45, 0), "Out", "Back", 0.5, true)
        task.delay(duration or 5, function() if nf and nf.Parent then dismissNotif() end end)
    end

    Stunts.notify = sendNotification
    Stunts.keyGui = keyGui

    local function isValidKey(input)
        for _, k in ipairs(VALID_KEYS) do
            if k == input then return true end
        end
        return false
    end

    local function trySaveKey(key)
        ENV[KEY_G_NAME] = key
        pcall(function()
            if writefile then writefile(KEY_SAVE_PATH, key) end
        end)
    end

    local function tryLoadSavedKey()
        local fromG = ENV[KEY_G_NAME]
        if fromG and fromG ~= "" then return fromG end
        local loaded = nil
        pcall(function()
            if isfile and isfile(KEY_SAVE_PATH) then
                local content = readfile(KEY_SAVE_PATH)
                if content and content ~= "" then loaded = content end
            end
        end)
        return loaded
    end

    local keyFrame    = nil
    local keyGlowVal  = 0
    local keyGlowDir  = 1
    local keyGlowConn = nil

    local function finishGate(ok)
        if gate.done then return end
        gate.ok   = ok
        gate.done = true
        ENV.M7_KeyAbort = nil
    end

    local function destroyKeyPanel(onDone, isCorrect)
        if keyGlowConn then keyGlowConn:Disconnect(); keyGlowConn = nil end
        if keyFrame and keyFrame.Parent then
            local fadeTime = isCorrect and 0.8 or 0.5
            for _, d in ipairs(keyFrame:GetDescendants()) do
                if d:IsA("TextLabel") or d:IsA("TextButton") or d:IsA("TextBox") then
                    pcall(function()
                        TweenService:Create(d, TweenInfo.new(fadeTime), {
                            BackgroundTransparency = 1, TextTransparency = 1
                        }):Play()
                    end)
                elseif d:IsA("Frame") then
                    pcall(function()
                        TweenService:Create(d, TweenInfo.new(fadeTime), {BackgroundTransparency = 1}):Play()
                    end)
                end
            end
            TweenService:Create(keyFrame, TweenInfo.new(fadeTime, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
                BackgroundTransparency = 1
            }):Play()
            task.delay(fadeTime + 0.05, function()
                if keyFrame and keyFrame.Parent then keyFrame:Destroy() end
                keyFrame = nil
                if onDone then onDone() end
            end)
        else
            if onDone then onDone() end
        end
    end

    ENV.M7_KeyAbort = function()
        if keyGlowConn then keyGlowConn:Disconnect(); keyGlowConn = nil end
        gate.ok, gate.done = false, true
        if keyGui then pcall(function() keyGui:Destroy() end) end
    end

    local function createKeyPanel()
        keyFrame = Instance.new("Frame", keyGui)
        keyFrame.Name                   = "KeyPanel"
        keyFrame.Size                   = UDim2.new(0, 290, 0, 175)
        keyFrame.Position               = UDim2.new(0.5, -145, 0.5, -87)
        keyFrame.BackgroundColor3       = Color3.fromRGB(0, 0, 0)
        keyFrame.BackgroundTransparency = 0.35
        keyFrame.BorderSizePixel        = 0
        keyFrame.ZIndex                 = 100
        Instance.new("UICorner", keyFrame).CornerRadius = UDim.new(0, 14)

        local keyStroke = Instance.new("UIStroke", keyFrame)
        keyStroke.Thickness       = 1.5
        keyStroke.Color           = Color3.fromRGB(160, 160, 160)
        keyStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

        keyGlowConn = RunService.Heartbeat:Connect(function(dt)
            keyGlowVal = keyGlowVal + keyGlowDir * dt * GLOW_SPEED
            if keyGlowVal >= 1 then keyGlowVal = 1; keyGlowDir = -1
            elseif keyGlowVal <= 0 then keyGlowVal = 0; keyGlowDir = 1 end
            local c = math.floor(160 + keyGlowVal * 95)
            if keyStroke and keyStroke.Parent then
                keyStroke.Color = Color3.fromRGB(c, c, c)
            end
        end)

        local closePanelBtn = Instance.new("TextButton", keyFrame)
        closePanelBtn.Size                   = UDim2.new(0, 14, 0, 14)
        closePanelBtn.Position               = UDim2.new(1, -17, 0, 4)
        closePanelBtn.BackgroundTransparency = 1
        closePanelBtn.Text                   = "X"
        closePanelBtn.TextColor3             = Color3.fromRGB(160, 160, 160)
        closePanelBtn.TextScaled             = true
        closePanelBtn.Font                   = Enum.Font.Michroma
        closePanelBtn.ZIndex                 = 105
        closePanelBtn.BorderSizePixel        = 0
        closePanelBtn.MouseButton1Click:Connect(function()
            destroyKeyPanel(function()
                finishGate(false)
                if keyGui then pcall(function() keyGui:Destroy() end) end
            end)
        end)

        local titleLbl = Instance.new("TextLabel", keyFrame)
        titleLbl.Size               = UDim2.new(0.85, 0, 0, 22)
        titleLbl.Position           = UDim2.new(0.075, 0, 0, 8)
        titleLbl.BackgroundTransparency = 1
        titleLbl.Text               = KEY_TITLE
        titleLbl.TextColor3         = Color3.fromRGB(255, 255, 255)
        titleLbl.Font               = Enum.Font.Michroma
        titleLbl.TextScaled         = true
        titleLbl.TextXAlignment     = Enum.TextXAlignment.Center
        titleLbl.ZIndex             = 101

        local divider = Instance.new("Frame", keyFrame)
        divider.Size                   = UDim2.new(0.7, 0, 0, 1)
        divider.Position               = UDim2.new(0.15, 0, 0, 34)
        divider.BackgroundTransparency = 1
        divider.BorderSizePixel        = 0
        divider.ZIndex                 = 101
        Instance.new("UICorner", divider).CornerRadius = UDim.new(1, 0)
        local divGrad = Instance.new("UIGradient", divider)
        divGrad.Color = ColorSequence.new({
            ColorSequenceKeypoint.new(0,   Color3.fromRGB(255, 255, 255)),
            ColorSequenceKeypoint.new(0.5, Color3.fromRGB(200, 200, 200)),
            ColorSequenceKeypoint.new(1,   Color3.fromRGB(120, 120, 120)),
        })

        task.spawn(function()
            local expanding = true
            while divider and divider.Parent do
                if expanding then
                    TweenService:Create(divider, TweenInfo.new(1.2, Enum.EasingStyle.Sine), {
                        Size = UDim2.new(0.82, 0, 0, 1), Position = UDim2.new(0.09, 0, 0, 34),
                        BackgroundTransparency = 0
                    }):Play()
                else
                    TweenService:Create(divider, TweenInfo.new(1.2, Enum.EasingStyle.Sine), {
                        Size = UDim2.new(0.5, 0, 0, 1), Position = UDim2.new(0.25, 0, 0, 34),
                        BackgroundTransparency = 0.2
                    }):Play()
                end
                expanding = not expanding
                task.wait(1.2)
            end
        end)

        local hintLbl = Instance.new("TextLabel", keyFrame)
        hintLbl.Size               = UDim2.new(0.88, 0, 0, 20)
        hintLbl.Position           = UDim2.new(0.06, 0, 0, 42)
        hintLbl.BackgroundTransparency = 1
        hintLbl.Text               = "اكتب المفتاح :"
        hintLbl.TextColor3         = Color3.fromRGB(180, 180, 180)
        hintLbl.Font               = Enum.Font.Gotham
        hintLbl.TextScaled         = true
        hintLbl.TextXAlignment     = Enum.TextXAlignment.Right
        hintLbl.ZIndex             = 101

        local inputFrame = Instance.new("Frame", keyFrame)
        inputFrame.Size                   = UDim2.new(0.88, 0, 0, 34)
        inputFrame.Position               = UDim2.new(0.06, 0, 0, 65)
        inputFrame.BackgroundColor3       = Color3.fromRGB(15, 15, 15)
        inputFrame.BackgroundTransparency = 0.2
        inputFrame.BorderSizePixel        = 0
        inputFrame.ZIndex                 = 101
        Instance.new("UICorner", inputFrame).CornerRadius = UDim.new(0, 8)
        local inputStroke = Instance.new("UIStroke", inputFrame)
        inputStroke.Thickness       = 1
        inputStroke.Color           = Color3.fromRGB(100, 100, 100)
        inputStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

        local inputBox = Instance.new("TextBox", inputFrame)
        inputBox.Size                   = UDim2.new(1, -10, 1, 0)
        inputBox.Position               = UDim2.new(0, 5, 0, 0)
        inputBox.BackgroundTransparency = 1
        inputBox.Text                   = ""
        inputBox.PlaceholderText        = "اكتب هنا ..."
        inputBox.PlaceholderColor3      = Color3.fromRGB(90, 90, 90)
        inputBox.TextColor3             = Color3.fromRGB(230, 230, 230)
        inputBox.Font                   = Enum.Font.GothamBold
        inputBox.TextScaled             = true
        inputBox.ClearTextOnFocus       = false
        inputBox.ZIndex                 = 102
        inputBox.TextXAlignment         = Enum.TextXAlignment.Right

        inputBox:GetPropertyChangedSignal("Text"):Connect(function()
            if inputBox.Text:match("[%a%d]") then
                inputBox.Font = Enum.Font.Michroma
            else
                inputBox.Font = Enum.Font.GothamBold
            end
        end)

        inputBox.Focused:Connect(function()
            TweenService:Create(inputStroke, TweenInfo.new(0.2), {Color = Color3.fromRGB(210, 210, 210), Thickness = 1.5}):Play()
            TweenService:Create(inputFrame,  TweenInfo.new(0.2), {BackgroundTransparency = 0.1}):Play()
        end)
        inputBox.FocusLost:Connect(function()
            TweenService:Create(inputStroke, TweenInfo.new(0.2), {Color = Color3.fromRGB(100, 100, 100), Thickness = 1}):Play()
            TweenService:Create(inputFrame,  TweenInfo.new(0.2), {BackgroundTransparency = 0.2}):Play()
        end)

        local resultLbl = Instance.new("TextLabel", keyFrame)
        resultLbl.Size               = UDim2.new(0.9, 0, 0, 18)
        resultLbl.Position           = UDim2.new(0.05, 0, 0, 103)
        resultLbl.BackgroundTransparency = 1
        resultLbl.Text               = ""
        resultLbl.TextColor3         = Color3.fromRGB(255, 80, 80)
        resultLbl.Font               = Enum.Font.GothamBold
        resultLbl.TextScaled         = true
        resultLbl.TextXAlignment     = Enum.TextXAlignment.Center
        resultLbl.ZIndex             = 102

        local CONF_W  = 130
        local CONF_H  = 28
        local CONF_PX = UDim2.new(0.5, -(CONF_W/2), 0, 128)

        local confirmBase = Instance.new("Frame", keyFrame)
        confirmBase.Size                   = UDim2.new(0, CONF_W, 0, CONF_H)
        confirmBase.Position               = CONF_PX
        confirmBase.BackgroundColor3       = Color3.fromRGB(255, 255, 255)
        confirmBase.BackgroundTransparency = 0
        confirmBase.BorderSizePixel        = 0
        confirmBase.ZIndex                 = 101
        Instance.new("UICorner", confirmBase).CornerRadius = UDim.new(0, 8)
        local confirmKeyStroke = Instance.new("UIStroke", confirmBase)
        confirmKeyStroke.Thickness       = 1.2
        confirmKeyStroke.Color           = Color3.fromRGB(180, 180, 180)
        confirmKeyStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

        local confirmKeyBtn = Instance.new("TextButton", confirmBase)
        confirmKeyBtn.Size                   = UDim2.new(1, 0, 1, 0)
        confirmKeyBtn.BackgroundTransparency = 1
        confirmKeyBtn.Text                   = "التأكد من المفتاح"
        confirmKeyBtn.TextColor3             = Color3.fromRGB(30, 30, 30)
        confirmKeyBtn.Font                   = Enum.Font.GothamBold
        confirmKeyBtn.TextScaled             = true
        confirmKeyBtn.ZIndex                 = 102
        confirmKeyBtn.BorderSizePixel        = 0

        confirmKeyBtn.MouseEnter:Connect(function()
            playClick()
            TweenService:Create(confirmBase, TweenInfo.new(0.15, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
                Size = UDim2.new(0, CONF_W+10, 0, CONF_H+5),
                Position = UDim2.new(0.5, -(CONF_W/2)-5, 0, 125),
                BackgroundColor3 = Color3.fromRGB(220, 220, 220),
            }):Play()
            TweenService:Create(confirmKeyStroke, TweenInfo.new(0.15), {Color = Color3.fromRGB(255, 255, 255)}):Play()
            task.delay(0.9, function()
                if confirmBase and confirmBase.Parent then
                    TweenService:Create(confirmBase, TweenInfo.new(0.2), {
                        Size = UDim2.new(0, CONF_W, 0, CONF_H), Position = CONF_PX,
                        BackgroundColor3 = Color3.fromRGB(255, 255, 255),
                    }):Play()
                    TweenService:Create(confirmKeyStroke, TweenInfo.new(0.15), {Color = Color3.fromRGB(180, 180, 180)}):Play()
                end
            end)
        end)
        confirmKeyBtn.MouseLeave:Connect(function()
            TweenService:Create(confirmBase, TweenInfo.new(0.15), {
                Size = UDim2.new(0, CONF_W, 0, CONF_H), Position = CONF_PX,
                BackgroundColor3 = Color3.fromRGB(255, 255, 255),
            }):Play()
            TweenService:Create(confirmKeyStroke, TweenInfo.new(0.15), {Color = Color3.fromRGB(180, 180, 180)}):Play()
        end)

        local resultGlowThread = nil
        local function stopResultGlow()
            if resultGlowThread then
                task.cancel(resultGlowThread)
                resultGlowThread = nil
            end
        end

        local function startCorrectGlow()
            stopResultGlow()
            resultGlowThread = task.spawn(function()
                while resultLbl and resultLbl.Parent do
                    TweenService:Create(resultLbl, TweenInfo.new(1.5), {TextColor3 = Color3.fromRGB(80, 255, 120)}):Play()
                    task.wait(1.5)
                    if not (resultLbl and resultLbl.Parent) then break end
                    TweenService:Create(resultLbl, TweenInfo.new(1.5), {TextColor3 = Color3.fromRGB(40, 180, 70)}):Play()
                    task.wait(1.5)
                end
            end)
        end

        local function startWrongGlow()
            stopResultGlow()
            resultGlowThread = task.spawn(function()
                while resultLbl and resultLbl.Parent and not keyVerified do
                    TweenService:Create(resultLbl, TweenInfo.new(0.6), {TextColor3 = Color3.fromRGB(255, 70, 70)}):Play()
                    task.wait(0.6)
                    if keyVerified then break end
                    TweenService:Create(resultLbl, TweenInfo.new(0.6), {TextColor3 = Color3.fromRGB(180, 50, 50)}):Play()
                    task.wait(0.6)
                end
            end)
        end

        local savedGlowThread = nil
        local function startSavedGlow()
            if savedGlowThread then task.cancel(savedGlowThread) end
            savedGlowThread = task.spawn(function()
                while inputBox and inputBox.Parent do
                    TweenService:Create(inputBox, TweenInfo.new(1.2), {TextColor3 = Color3.fromRGB(255, 255, 255)}):Play()
                    task.wait(1.2)
                    if not (inputBox and inputBox.Parent) then break end
                    TweenService:Create(inputBox, TweenInfo.new(1.2), {TextColor3 = Color3.fromRGB(140, 140, 140)}):Play()
                    task.wait(1.2)
                end
            end)
        end

        task.spawn(function()
            local loaded = tryLoadSavedKey()
            if loaded and loaded ~= "" then
                inputBox.Text       = loaded
                inputBox.Font       = Enum.Font.Michroma
                inputBox.TextColor3 = Color3.fromRGB(255, 255, 255)
                if isValidKey(loaded) then
                    startSavedGlow()
                else
                    resultLbl.Text       = "X - المفتاح المحفوظ خاطئ أو تغيّر"
                    resultLbl.TextColor3 = Color3.fromRGB(255, 70, 70)
                    startWrongGlow()
                end
            end
        end)

        local checkDebounce = false
        local function checkKey()
            if checkDebounce then return end
            checkDebounce = true
            playClick()

            TweenService:Create(confirmBase, TweenInfo.new(0.08, Enum.EasingStyle.Back), {
                Size = UDim2.new(0, CONF_W+8, 0, CONF_H+4),
                Position = UDim2.new(0.5, -(CONF_W/2)-4, 0, 126),
                BackgroundColor3 = Color3.fromRGB(160, 160, 160),
            }):Play()
            task.delay(0.18, function()
                if confirmBase and confirmBase.Parent then
                    TweenService:Create(confirmBase, TweenInfo.new(0.15, Enum.EasingStyle.Back), {
                        Size = UDim2.new(0, CONF_W, 0, CONF_H), Position = CONF_PX,
                        BackgroundColor3 = Color3.fromRGB(255, 255, 255),
                    }):Play()
                end
            end)

            local typed = inputBox.Text
            if isValidKey(typed) then
                stopResultGlow()
                resultLbl.TextColor3 = Color3.fromRGB(80, 255, 120)
                resultLbl.Text       = "المفتاح صحيح, جاري التحميل... - ✓"
                startCorrectGlow()
                TweenService:Create(confirmBase, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(200, 255, 210)}):Play()
                trySaveKey(typed)
                task.delay(1.2, function()
                    keyVerified = true
                    destroyKeyPanel(function()
                        task.spawn(function()
                            sendNotification("تم تفعيل السكربت بنجاح", 6)
                        end)
                        finishGate(true)
                    end, true)
                end)
            else
                stopResultGlow()
                resultLbl.TextColor3 = Color3.fromRGB(255, 70, 70)
                resultLbl.Text       = "X - المفتاح خاطئ، حاول مرة ثانية"
                startWrongGlow()

                if inputBox.Text ~= "" then
                    TweenService:Create(inputBox, TweenInfo.new(0.35, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
                        TextTransparency = 1
                    }):Play()
                    task.delay(0.37, function()
                        if inputBox and inputBox.Parent then
                            inputBox.Text             = ""
                            inputBox.TextTransparency = 0
                            inputBox.Font             = Enum.Font.GothamBold
                        end
                    end)
                end

                task.delay(0.5, function() checkDebounce = false end)
            end
        end

        confirmKeyBtn.MouseButton1Click:Connect(checkKey)
        inputBox.FocusLost:Connect(function(enterPressed)
            if enterPressed then checkKey() end
        end)

        -- دخل بتغيير السيرفر من السكربت والتفريم كان مفعّل: يأكد المفتاح المحفوظ تلقائياً
        if HOP.arrived and HOP.set.farm then
            task.delay(1.2, function()
                if inputBox and inputBox.Parent and inputBox.Text ~= "" then checkKey() end
            end)
        end
    end

    -- دخل بتغيير السيرفر من السكربت + وضع تغيير السيرفر مفعّل + المفتاح المحفوظ صحيح:
    -- يتخطى القائمة تماماً (بدون قائمة، بدون صوت، بدون إشعار)
    -- لو دخلت انت بنفسك (HOP.arrived = false) تطلع لك قائمة المفاتيح عادي
    if HOP.arrived and HOP.set.farm and HOP.set.hop then
        local saved = tryLoadSavedKey()
        if saved and isValidKey(saved) then
            keyVerified = true
            finishGate(true)
        end
    end
    if not gate.done then createKeyPanel() end

    while not gate.done do
        task.wait(0.1)
    end
    keyOk = gate.ok
end

if not keyOk then return end
-- =============================================
-- نهاية نظام المفاتيح
-- =============================================

-- =============================================
-- الإعدادات
-- =============================================
local CFG = {
    POS_START       = Vector3.new(1191.67, 17.24, 3649.43),   -- مكان الغسيل (يدور على برومبت الغسيل حواليه)
    POS_BUY         = Vector3.new(1191.67, 17.24, 3649.43),   -- مكان شراء الأداة (غيّره لو إحداثياته غير مكان الغسيل)
    BUY_RANGE       = 40,                                     -- ما يرسل حزمة الشراء إلا لو هو داخل هذي المسافة من POS_BUY

    -- تغيير السيرفر تلقائياً
    HOP_MIN_PLAYERS = 0,                      -- أقل عدد لاعبين مقبول (0 = أقل سيرفر ممكن، لو يوقعك بسيرفرات ميتة رجّعه 1)
    HOP_MAX_PLAYERS = 6,                      -- أقصى عدد لاعبين يفضّله (لو ما لقى سيرفر بهالعدد يرخّي الشرط تدريجياً)
    HOP_PICK_TOP    = 5,                      -- يختار عشوائي من أقل كم سيرفر (عشان ما يتزاحم الكل على نفس السيرفر)
    HOP_RETRY       = 20,                     -- لو فشل التغيير يعيد كل كم ثانية وهو بمكان الانتظار
    HOP_AFTER_WASH  = 3,                      -- ينتظر بعد الغسيل قبل تغيير السيرفر
    AUTOSTART_DELAY = 2,                      -- بعد دخول السيرفر الجديد ينتظر هذي المدة ثم يبدأ تلقائي
    USE_QUEUE       = true,                   -- يسجّل السكربت يشتغل لحاله بعد الانتقال (queue_on_teleport)
                                              -- (لو منفذك فيه autoexec خله false عشان ما يشتغل مرتين)
    SCRIPT_FILE     = "M7_Farm.lua",          -- اسم ملف السكربت في مجلد workspace للمنفذ
    SCRIPT_URL      = "",                     -- أو رابط raw للسكربت (لو عبّيته يُستخدم بدل الملف)
    POS_WAIT        = Vector3.new(-5.8, 7.0, 4006.7),         -- مكان الانتظار
    POS_HACK        = Vector3.new(-195.73, 7.07, 5346.06),
    POS_ATM2        = Vector3.new(1145.28, 7.07, 289.75),
    POS_ATM3        = Vector3.new(598.2, 8.0, -115.4),
    POS_ATM4        = Vector3.new(1585.3, 13.4, 2809.1),      -- الصراف الرابع
    ATM4_LIFT       = Vector3.new(0, 0, 0),
    MENU_DELAY      = 1.2,
    EXPERT_DELAY    = 0.5,
    PRESS_INTERVAL  = 1.75,
    ATM_TIMEOUT     = 9,
    TAMPER_TEXT     = "عبث",
    TOOL_NAME       = "أداة اختراق",
    LEVEL_TEXT      = "خبير",
    PROMPT_MAX_FAR  = 300,
    CLICK_VERIFY    = 1.2,

    STREAM_TIMEOUT  = 4,

    GAME_START_WAIT = 25,
    GAME_MAX_WAIT   = 120,

    SUCCESS_TEXTS   = {"نجح الاختراق", "تم الاختراق", "غير مغسولة", "ستحول تلقائي"},
    RESULT_WAIT     = 10,

    ATM_RETRIES     = 3,
    RESUME_GAME_WAIT = 8,
    COUNT_ENDED_AS_SUCCESS = false,
    STATE_MAX_AGE   = 900,

    -- تحويل الفلوس
    WASH_STAY         = 10,                   -- أقصى وقت انتظار عند برومبت الغسيل (ثواني)
    WASH_CONFIRM      = 3,                    -- بعد ما يشوف دليل التحويل يكمل يضغط هذي المدة (وما يتعدى WASH_STAY)
    WASH_FIND         = 8,                    -- أقصى وقت يدور فيه على برومبت الغسيل قبل ما يحكم إن ما فيه فلوس
    WASH_RETRIES      = 3,                    -- عدد محاولات الانتقال والغسل بالجولة الوحدة
    WASH_ROUNDS       = 3,                    -- عدد الجولات قبل ما يكمل (ويحاول مرة ثانية بعدين)
    WASH_TP_WAIT      = 0.3,
    WASH_PRESS_GAP    = 0.35,                 -- كل كم ثانية يعيد الضغط التلقائي
    WASH_NEAR_START   = 15,                   -- لو ابتعد عن مكان الغسيل أكثر من هذا وقت البحث يرجعه
    WASH_ANCHOR_TOL   = 8,                    -- لو ابتعد عن البرومبت أكثر من هذا وقت الغسل يرجعه
    WASH_BUY_TIMEOUT  = 20,                   -- أقصى وقت لشراء الأداة بعد الغسيل
    WASH_AFTER        = 1.0,                  -- بعد الشراء يقعد هذي المدة ثم يكمل
    WASH_PROMPT_TEXTS = {"غسل", "مغسل"},      -- نص البرومبت / زر الشاشة
    WASH_PROMPT_NAMES = {"StartProximity"},   -- اسم احتياطي
    WASH_PROMPT_RANGE = 150,
    WASH_PROMPT_NEAR  = 80,
    WASH_FALLBACK_RANGE = 25,                 -- احتياط: أي برومبت قريب بهالمسافة مو نصه شراء (بعد نص مدة البحث)
    WASH_DUMP_RANGE   = 60,                   -- يطبع البرومبتات القريبة بهالمسافة لو ما لقى برومبت غسيل
    WASH_TEXTS        = {"مقابل"},            -- كلمة إشعار تحويل الفلوس
    WASH_IGNORE       = {"أداة", "اختراق"},   -- أي إشعار فيه هذي الكلمات ما يُحسب غسيل (مثل "تم شراء أداة اختراق مقابل 800")
    BUY_PROMPT_TEXTS  = {"شراء", "أداة", "اختراق"},   -- لو البرومبت صار نصه شراء أداة ما يضغطه وقت الغسيل
    WASH_BTN_MAX_DIST = 160,                  -- أقصى بُعد (بكسل) بين نص الغسل وزره

    -- انتظار الصرافات
    ATM_COOLDOWN     = 120,
    ATM_FAIL_RETRY   = 15,
    DETECT_OPEN      = true,
    DETECT_RADIUS    = 30,
    DETECT_MIN_AGE   = 20,
    WAIT_POLL        = 0.4,

    DOTS_INTERVAL    = 0.25,

    WORD_MIN        = 3,
    WORD_MAX        = 14,
    WORD_ASCII      = true,
    ROW_TOL         = 12,
    IDLE_SCAN       = 0.3,
    RETRY_AFTER     = 0.15,
    MAX_ATTEMPTS    = 10,
    MAX_PER_TICK    = 8,
    GROUND_MARGIN   = 60,
    END_AFTER       = 4,

    -- حماية الضغط: يمنع الضغط على أي شي برا قائمة اللعبة
    SAFE_CLICK      = true,

    DEBUG           = true,
}

local PKT_BUY  = "oe\003buy"
local PKT_LVL3 = "kb\003"
local PKT_HACK = "o`\004hack"

-- =============================================
-- الحالة المحفوظة
-- =============================================
local STATE = ENV.M7_State
if type(STATE) ~= "table" then
    STATE = {}
    ENV.M7_State = STATE
end
STATE.closed      = (type(STATE.closed) == "table") and STATE.closed or {0, 0, 0, 0}
STATE.block       = (type(STATE.block) == "table") and STATE.block or {0, 0, 0, 0}
STATE.gameStart   = STATE.gameStart or 0
STATE.ts          = STATE.ts or 0
STATE.needWash    = STATE.needWash or false
STATE.stole       = STATE.stole or false   -- سرق فلوس ولسا ما انغسلت (عشان ما يحكم "ما فيه فلوس" بسرعة)

-- سيرفر جديد: نصفّر مؤقتات الصرافات (كانت من السيرفر القديم) ونحتفظ بحالة الغسيل لو كان وسطه
if STATE.jobId ~= game.JobId then
    STATE.jobId = game.JobId
    STATE.closed = {0, 0, 0, 0}
    STATE.block = {0, 0, 0, 0}
    STATE.stage = nil
    STATE.atmIdx = nil
    STATE.gameStart = 0
    if STATE.phase ~= "wash" then STATE.phase = nil end
end

local function touch() STATE.ts = os.time() end

local function resetState()
    STATE.phase = nil
    STATE.atmIdx = nil
    STATE.stage = nil
    STATE.gameStart = 0
    touch()
end

if STATE.phase == "atm" and os.time() - (STATE.ts or 0) > CFG.STATE_MAX_AGE then
    resetState()
end

-- =============================================
-- الحالة العامة
-- =============================================
local running, token = false, 0
local myGui = nil
local setStatus = function() end
local stopAll = function() end

local W = {active = false, sessions = 0}
-- WM: دوال تحويل الفلوس (جدول واحد عشان حد المتغيرات المحلية)
-- buyLock: لو true، حزمة شراء أداة الاختراق تنقفل ولا تنرسل أبداً (أثناء الغسيل)
-- washDone: لو true، الضغط على برومبت الغسيل متوقف (انتأكد الغسيل)
local WM = {sweepDone = false, buyLock = false, washDone = false, dis = {}}
local FZ = {on = false}          -- تجميد حركة اللاعب

local IS_MOBILE = UIS.TouchEnabled and not UIS.MouseEnabled

local function dbg(...)
    if CFG.DEBUG then print("[M7]", ...) end
end

local function alive(tk) return running and token == tk end

local function waitUntil(cond, timeout, tk)
    local t0 = os.clock()
    while alive(tk) and os.clock() - t0 < timeout do
        if cond() then return true end
        task.wait(0.1)
    end
    return cond() and true or false
end

-- =============================================
-- ريموت + اللاعب
-- =============================================
local remoteCache = nil
local function getRemote()
    if remoteCache and remoteCache.Parent then return remoteCache end
    local ok, r = pcall(function()
        return RS:WaitForChild("Packages", 5):WaitForChild("Packet", 5):WaitForChild("RemoteEvent", 5)
    end)
    if ok and r then remoteCache = r end
    return remoteCache
end

local function fireGame(pkt)
    -- قفل حزمة شراء الأداة أثناء غسيل الفلوس + ما يشتري إلا عند مكان الشراء
    if pkt == PKT_BUY then
        if WM.buyLock then
            dbg("حزمة الشراء مقفولة (وقت الغسيل)")
            return false
        end
        local ch = player.Character
        local hrp = ch and ch:FindFirstChild("HumanoidRootPart")
        if hrp and (hrp.Position - CFG.POS_BUY).Magnitude > CFG.BUY_RANGE then
            dbg("حزمة الشراء ممنوعة: مو عند مكان الشراء")
            return false
        end
    end
    local r = getRemote()
    if not r then dbg("ما لقيت RemoteEvent") return false end
    local ok, err = pcall(function() r:FireServer(buffer.fromstring(pkt)) end)
    if not ok then dbg("فشل الإرسال:", err) end
    return ok
end

local function getChar() return player.Character end
local function getHum()
    local c = player.Character
    return c and c:FindFirstChildOfClass("Humanoid")
end
local function getHRP()
    local c = player.Character
    return c and c:FindFirstChild("HumanoidRootPart")
end

-- =============================================
-- تغيير السيرفر: يدخل سيرفر فاضي / فيه لاعبين قليل (مرتّب من الأقل)
-- ويتجاهل آخر السيرفرات اللي دخلها
-- =============================================
function HOP.get(url)
    local body
    local ok = pcall(function() body = game:HttpGet(url) end)
    if ok and type(body) == "string" and body ~= "" then return body end
    local req = (syn and syn.request) or (http and http.request) or http_request or request
    if req then
        local ok2, res = pcall(req, {Url = url, Method = "GET"})
        if ok2 and type(res) == "table" and res.Body
            and (res.StatusCode == nil or res.StatusCode == 200) then
            return res.Body
        end
    end
    return nil
end

-- maxP: أقصى عدد لاعبين مقبول (nil = بدون حد)
function HOP.candidates(ignoreSeen, maxP)
    local list, cursor = {}, nil
    local seen = {}
    if not ignoreSeen then
        for _, id in ipairs(HOP.set.seen or {}) do seen[id] = true end
    end
    for _ = 1, 8 do
        local url = "https://games.roblox.com/v1/games/" .. game.PlaceId
            .. "/servers/Public?sortOrder=Asc&excludeFullGames=true&limit=100"
        if cursor then url = url .. "&cursor=" .. cursor end
        local body = HOP.get(url)
        if not body then break end
        local ok, data = pcall(function() return HOP.http:JSONDecode(body) end)
        if (not ok) or type(data) ~= "table" or type(data.data) ~= "table" then break end
        for _, s in ipairs(data.data) do
            if s.id ~= game.JobId and not seen[s.id]
                and type(s.playing) == "number" and type(s.maxPlayers) == "number"
                and s.playing >= CFG.HOP_MIN_PLAYERS
                and s.playing <= (maxP or 9999)
                and s.maxPlayers - s.playing >= 2 then
                list[#list + 1] = s
            end
        end
        cursor = data.nextPageCursor
        if type(cursor) ~= "string" or cursor == "" then break end
        if #list >= 60 then break end
    end
    table.sort(list, function(a, b)
        if a.playing ~= b.playing then return a.playing < b.playing end
        if a.maxPlayers ~= b.maxPlayers then return a.maxPlayers < b.maxPlayers end
        return tostring(a.id) < tostring(b.id)
    end)
    -- يخلط أقل كم سيرفر عشان ما يتزاحم كل اللي يستخدمون السكربت على نفس السيرفر
    local top = math.min(CFG.HOP_PICK_TOP or 1, #list)
    for i = top, 2, -1 do
        local j = math.random(1, i)
        list[i], list[j] = list[j], list[i]
    end
    return list
end

function HOP.queue()
    if HOP.queued or not CFG.USE_QUEUE then return end
    local q = queue_on_teleport or (syn and syn.queue_on_teleport)
    if not q then
        dbg("تحذير: المنفذ ما يدعم queue_on_teleport، شغّل السكربت يدوي بعد التغيير")
        return
    end
    local code
    if CFG.SCRIPT_URL ~= "" then
        code = 'loadstring(game:HttpGet("' .. CFG.SCRIPT_URL .. '"))()'
    else
        code = 'loadstring(readfile("' .. CFG.SCRIPT_FILE .. '"))()'
    end
    if pcall(q, code) then HOP.queued = true end
end

function HOP.go(tk)
    if HOP.busy then return false end
    HOP.busy = true
    setStatus("تغيير السيرفر...")
    -- يبدأ بالسيرفرات الأقل لاعبين، ولو ما لقى يرخّي الشرط تدريجياً
    local list = HOP.candidates(false, CFG.HOP_MAX_PLAYERS)
    if #list == 0 then list = HOP.candidates(true, CFG.HOP_MAX_PLAYERS) end
    if #list == 0 then list = HOP.candidates(false) end
    if #list == 0 then list = HOP.candidates(true) end
    if (not alive(tk)) or #list == 0 then
        HOP.busy = false
        if alive(tk) then dbg("التغيير: ما لقيت سيرفر مناسب") end
        return false
    end
    HOP.queue()

    local idx, conn = 1, nil
    local function try()
        local s = list[idx]
        if not s then HOP.busy = false; return end
        setStatus("تغيير السيرفر...")
        dbg("التغيير: ينتقل لسيرفر", s.id, "لاعبين:", s.playing)
        -- يسجّل إنه هو اللي قاصد هذا السيرفر (عشان يفرّق بين تغيير السكربت ودخولك اليدوي)
        HOP.set.hopJob = s.id
        HOP.set.hopAt = os.time()
        HOP.set.expect = s.playing
        HOP.set.farm = true
        HOP.set.hop = true
        HOP.save()
        pcall(function()
            HOP.tp:TeleportToPlaceInstance(game.PlaceId, s.id, player, nil, {m7hop = true})
        end)
    end
    conn = HOP.tp.TeleportInitFailed:Connect(function(plr, result, msg)
        if plr ~= player then return end
        dbg("التغيير: فشل الانتقال:", tostring(result), tostring(msg))
        idx = idx + 1
        if idx > #list or idx > 30 then
            if conn then conn:Disconnect() end
            HOP.busy = false
            return
        end
        task.wait(0.5)
        try()
    end)
    task.delay(40, function()
        if conn then pcall(function() conn:Disconnect() end) end
        HOP.busy = false
    end)
    try()
    return true
end

-- =============================================
-- قفل على مستوى الريموت: أي حزمة فيها "buy" تنحجب وقت الغسيل
-- (تغطي أي مصدر: السكربت أو سكربتات اللعبة نفسها)
-- =============================================
function WM.installHook()
    ENV.M7_IsBuyLocked = function() return WM.buyLock end
    ENV.M7_OnBlocked = function(tb)
        dbg("⛔ انحجبت حزمة شراء وقت الغسيل. المصدر:\n" .. tostring(tb))
    end
    if ENV.M7_HookDone == game.JobId then return end
    if not (hookmetamethod and getnamecallmethod) then
        dbg("تحذير: المنفذ ما يدعم hookmetamethod، القفل على مستوى السكربت فقط")
        return
    end
    local old
    local function handler(self, ...)
        local method = getnamecallmethod()
        if method == "FireServer" and ENV.M7_IsBuyLocked and ENV.M7_IsBuyLocked() then
            local a = ...
            local s = nil
            if typeof(a) == "buffer" then
                pcall(function() s = buffer.tostring(a) end)
            end
            if s and string.find(s, "buy", 1, true) then
                if ENV.M7_OnBlocked then pcall(ENV.M7_OnBlocked, debug.traceback()) end
                return nil
            end
        end
        return old(self, ...)
    end
    local ok, err = pcall(function()
        old = hookmetamethod(game, "__namecall", newcclosure and newcclosure(handler) or handler)
    end)
    if ok and old then
        ENV.M7_HookDone = game.JobId
        dbg("قفل الريموت اشتغل")
    else
        dbg("تحذير: فشل قفل الريموت:", err)
    end
end

-- =============================================
-- تجميد حركة اللاعب طول ما التفريم شغال
-- (يعطّل التحكم + يثبّت السرعة والقفز على صفر، والانتقال بالسكربت يشتغل عادي)
-- =============================================
function FZ.start()
    if FZ.on then return end
    FZ.on = true
    FZ.hum, FZ.orig = nil, nil

    pcall(function()
        local ps = player:FindFirstChild("PlayerScripts")
        local pm = ps and ps:FindFirstChild("PlayerModule")
        if pm then
            FZ.controls = require(pm):GetControls()
            FZ.controls:Disable()
        end
    end)

    FZ.conn = RunService.Heartbeat:Connect(function()
        local hum = getHum()
        if not hum then return end
        if FZ.hum ~= hum then
            FZ.hum = hum
            FZ.orig = {ws = hum.WalkSpeed, jp = hum.JumpPower, jh = hum.JumpHeight}
            if FZ.orig.ws <= 0 then FZ.orig.ws = 16 end
        end
        if hum.WalkSpeed ~= 0 then hum.WalkSpeed = 0 end
        if hum.UseJumpPower then
            if hum.JumpPower ~= 0 then hum.JumpPower = 0 end
        elseif hum.JumpHeight ~= 0 then
            hum.JumpHeight = 0
        end
    end)
end

function FZ.stop()
    if not FZ.on then return end
    FZ.on = false
    if FZ.conn then
        pcall(function() FZ.conn:Disconnect() end)
        FZ.conn = nil
    end
    pcall(function()
        if FZ.controls then FZ.controls:Enable() end
    end)
    FZ.controls = nil
    local hum = getHum()
    if hum and FZ.orig then
        pcall(function()
            hum.WalkSpeed = FZ.orig.ws
            if hum.UseJumpPower then
                hum.JumpPower = FZ.orig.jp
            else
                hum.JumpHeight = FZ.orig.jh
            end
        end)
    end
    FZ.hum, FZ.orig = nil, nil
end

-- =============================================
-- سجل النصوص
-- =============================================
local texts, gameSet = {}, {}
local regConns, regOn = {}, false
local gameGuiRef = nil

local function addText(d)
    if not (d:IsA("TextLabel") or d:IsA("TextButton")) then return end
    if myGui and d:IsDescendantOf(myGui) then return end
    texts[d] = true
    if gameGuiRef and d:IsDescendantOf(gameGuiRef) then gameSet[d] = true end
end

local function ensureRegistry()
    if regOn then return end
    local pg = player:FindFirstChildOfClass("PlayerGui")
    if not pg then return end
    regOn = true
    regConns[#regConns + 1] = pg.DescendantAdded:Connect(addText)
    regConns[#regConns + 1] = pg.DescendantRemoving:Connect(function(d)
        texts[d] = nil
        gameSet[d] = nil
    end)
    task.spawn(function()
        local n = 0
        for _, d in ipairs(pg:GetDescendants()) do
            addText(d)
            n = n + 1
            if n % 2500 == 0 then task.wait() end
        end
    end)
end

local function stopRegistry()
    regOn = false
    for _, c in ipairs(regConns) do pcall(function() c:Disconnect() end) end
    regConns = {}
    texts, gameSet, gameGuiRef = {}, {}, nil
end

local function isShown(obj)
    local o = obj
    while o do
        if o:IsA("GuiObject") then
            if not o.Visible then return false end
        elseif o:IsA("ScreenGui") then
            return o.Enabled
        end
        o = o.Parent
    end
    return false
end

-- =============================================
-- نوكليب
-- =============================================
local ncConn, ncOrig, ncParts, ncAcc = nil, {}, {}, 0

local function rebuildParts()
    ncParts = {}
    local c = player.Character
    if not c then return end
    for _, d in ipairs(c:GetDescendants()) do
        if d:IsA("BasePart") then ncParts[#ncParts + 1] = d end
    end
end

local function setNoclip(on)
    if on then
        if ncConn then return end
        rebuildParts()
        ncAcc = 0
        ncConn = RunService.Stepped:Connect(function(_, dt)
            ncAcc = ncAcc + dt
            if ncAcc > 1 then ncAcc = 0; rebuildParts() end
            for i = 1, #ncParts do
                local p = ncParts[i]
                if p.Parent and p.CanCollide then
                    ncOrig[p] = true
                    p.CanCollide = false
                end
            end
        end)
    else
        if ncConn then ncConn:Disconnect(); ncConn = nil end
        for p, v in pairs(ncOrig) do
            if p and p.Parent then pcall(function() p.CanCollide = v end) end
        end
        ncOrig = {}
    end
end

-- =============================================
-- انتقال
-- =============================================
local function teleport(pos)
    local char, hrp = getChar(), getHRP()
    if not (char and hrp) then return false end
    local hum = getHum()
    if hum and hum.SeatPart then
        pcall(function() hum.Sit = false end)
        task.wait(0.15)
    end
    pcall(function()
        hrp.AssemblyLinearVelocity = Vector3.zero
        hrp.AssemblyAngularVelocity = Vector3.zero
        char:PivotTo(CFrame.new(pos))
    end)
    return true
end

-- =============================================
-- الأداة
-- =============================================
local function isHackTool(t)
    if not t:IsA("Tool") then return false end
    if string.find(t.Name, CFG.TOOL_NAME, 1, true) then return true end
    local tip = t.ToolTip
    return tip ~= nil and tip ~= "" and string.find(tip, CFG.TOOL_NAME, 1, true) ~= nil
end

local function findToolIn(container)
    if not container then return nil end
    for _, t in ipairs(container:GetChildren()) do
        if isHackTool(t) then return t end
    end
    return nil
end

local function toolInHand() return findToolIn(player.Character) end
local function toolInBag() return findToolIn(player:FindFirstChildOfClass("Backpack")) end
local function hasTool() return (toolInHand() or toolInBag()) ~= nil end

local function equipNow()
    if toolInHand() then return true end
    local t, hum = toolInBag(), getHum()
    if t and hum and t.Parent then
        pcall(function() hum:EquipTool(t) end)
    end
    return toolInHand() ~= nil
end

local keepConns = {}
local function clearKeep()
    for _, c in ipairs(keepConns) do pcall(function() c:Disconnect() end) end
    keepConns = {}
end

local function reequipSoon()
    task.defer(function()
        if not running then return end
        task.wait(0.05)
        if running then equipNow() end
    end)
end

local function hookChar(char)
    keepConns[#keepConns + 1] = char.ChildRemoved:Connect(function(ch)
        if running and isHackTool(ch) then reequipSoon() end
    end)
end

local function hookBackpack(bp)
    keepConns[#keepConns + 1] = bp.ChildAdded:Connect(function(ch)
        if running and isHackTool(ch) then reequipSoon() end
    end)
end

local function startKeepTool()
    clearKeep()
    if player.Character then hookChar(player.Character) end
    local bp = player:FindFirstChildOfClass("Backpack")
    if bp then hookBackpack(bp) end
    keepConns[#keepConns + 1] = player.CharacterAdded:Connect(function(c)
        hookChar(c)
        local b = player:FindFirstChildOfClass("Backpack")
        if b then hookBackpack(b) end
    end)
end

-- =============================================
-- البرومبتات (+ انستنت برومبت)
-- =============================================
local prompts, promptConns = {}, {}
local posCache = setmetatable({}, {__mode = "k"})

local function makeInstant(p)
    pcall(function()
        if p.HoldDuration ~= 0 then p.HoldDuration = 0 end
        p.RequiresLineOfSight = false
    end)
end

local function trackPrompt(p)
    prompts[p] = true
    makeInstant(p)
end

local function startPromptTracking()
    for _, c in ipairs(promptConns) do pcall(function() c:Disconnect() end) end
    promptConns = {}
    promptConns[#promptConns + 1] = workspace.DescendantAdded:Connect(function(d)
        if d:IsA("ProximityPrompt") then trackPrompt(d) end
    end)
    promptConns[#promptConns + 1] = workspace.DescendantRemoving:Connect(function(d)
        if d:IsA("ProximityPrompt") then
            prompts[d] = nil
            posCache[d] = nil
        end
    end)
    task.spawn(function()
        local n = 0
        for _, d in ipairs(workspace:GetDescendants()) do
            if d:IsA("ProximityPrompt") then trackPrompt(d) end
            n = n + 1
            if n % 3000 == 0 then task.wait() end
        end
    end)
end

local function stopPromptTracking()
    for _, c in ipairs(promptConns) do pcall(function() c:Disconnect() end) end
    promptConns = {}
    prompts = {}
    posCache = setmetatable({}, {__mode = "k"})
end

local function rescanPrompts()
    pcall(function()
        local n = 0
        for _, d in ipairs(workspace:GetDescendants()) do
            if d:IsA("ProximityPrompt") and not prompts[d] then trackPrompt(d) end
            n = n + 1
            if n % 4000 == 0 then task.wait() end
        end
    end)
end

local function promptPos(p)
    local c = posCache[p]
    if c then return c end
    local par = p.Parent
    if not par then return nil end
    if par:IsA("BasePart") then
        local pos = par.Position
        if par.Anchored then posCache[p] = pos end
        return pos
    end
    if par:IsA("Attachment") then return par.WorldPosition end
    if par:IsA("Model") then
        local ok, cf = pcall(function() return par:GetPivot() end)
        if ok and cf then return cf.Position end
    end
    return nil
end

-- v40: نفحص ActionText فقط. ObjectText = "مغسلة أموال" يظهر حتى لو البرومبت صار "شراء أداة اختراق (800)"
-- (هذا كان سبب إن السكربت يحسب برومبت الشراء كبرومبت غسيل ويضغطه)
local function isWashPrompt(p)
    local a = tostring(p.ActionText)
    for _, k in ipairs(CFG.BUY_PROMPT_TEXTS) do
        if string.find(a, k, 1, true) then return false end
    end
    for _, k in ipairs(CFG.WASH_PROMPT_TEXTS) do
        if string.find(a, k, 1, true) then return true end
    end
    return false
end

local function nearestPrompt()
    local hrp = getHRP()
    if not hrp then return nil end
    local origin = hrp.Position
    local best, bd = nil, CFG.PROMPT_MAX_FAR
    for p in pairs(prompts) do
        if p.Parent and p.Enabled then
            local pos = promptPos(p)
            if pos then
                local d = (pos - origin).Magnitude
                if d < bd and not isWashPrompt(p) then best, bd = p, d end
            end
        end
    end
    return best, bd
end

local function pressPrompt(p)
    makeInstant(p)
    local pos, hrp = promptPos(p), getHRP()
    if pos and hrp then
        local reach = p.MaxActivationDistance or 10
        if (hrp.Position - pos).Magnitude > reach - 1.5 then
            teleport(pos + Vector3.new(0, 2, 0))
            task.wait(0.15)
        end
    end
    if fireproximityprompt then
        if pcall(fireproximityprompt, p) then return true end
    end
    return (pcall(function()
        p:InputHoldBegin()
        task.wait()
        p:InputHoldEnd()
    end))
end

local function atmPromptOpen(pos)
    for p in pairs(prompts) do
        if p.Parent and p.Enabled then
            local pp = promptPos(p)
            if pp and (pp - pos).Magnitude <= CFG.DETECT_RADIUS then
                return true
            end
        end
    end
    return false
end

-- =============================================
-- الضغط على الواجهات (5 طرق) + حماية الضغط برا القائمة
-- =============================================
local function centerOf(obj)
    local ap, as = obj.AbsolutePosition, obj.AbsoluteSize
    return ap.X + as.X / 2, ap.Y + as.Y / 2
end

local function fakeInput(x, y, state)
    return {
        UserInputType = IS_MOBILE and Enum.UserInputType.Touch or Enum.UserInputType.MouseButton1,
        UserInputState = state,
        Position = Vector3.new(x, y, 0),
        Delta = Vector3.zero,
        KeyCode = Enum.KeyCode.Unknown,
    }
end

local btnCache = setmetatable({}, {__mode = "k"})

local function getButton(obj)
    local c = btnCache[obj]
    if c and c.b and c.b.Parent and (c.anc or os.clock() - c.t < 0.2) then
        return c.b
    end
    local sg = obj:FindFirstAncestorOfClass("ScreenGui")
    local b, anc = nil, false
    local o = obj
    while o and o ~= sg do
        if o:IsA("GuiButton") then b, anc = o, true; break end
        o = o.Parent
    end
    if not b and sg then
        local cx, cy = centerOf(obj)
        local ba = math.huge
        local scope = obj
        for _ = 1, 3 do
            if scope.Parent and scope.Parent ~= sg and not scope.Parent:IsA("PlayerGui") then
                scope = scope.Parent
            else
                break
            end
        end
        for _, d in ipairs(scope:GetDescendants()) do
            if d:IsA("GuiButton") and d.Visible then
                local p, s = d.AbsolutePosition, d.AbsoluteSize
                if cx >= p.X and cx <= p.X + s.X and cy >= p.Y and cy <= p.Y + s.Y then
                    local a = s.X * s.Y
                    if a < ba then b, ba = d, a end
                end
            end
        end
    end
    btnCache[obj] = {b = b, anc = anc, t = os.clock()}
    return b
end

local function connFire(sig, ...)
    if not (getconnections and sig) then return 0 end
    local args = table.pack(...)
    local okL, list = pcall(getconnections, sig)
    if not okL or type(list) ~= "table" then return 0 end
    local n = 0
    for _, c in ipairs(list) do
        local ok = pcall(function() c:Fire(table.unpack(args, 1, args.n)) end)
        if not ok then
            ok = pcall(function() c.Function(table.unpack(args, 1, args.n)) end)
        end
        if ok then n = n + 1 end
    end
    return n
end

local function hasVIM()
    return (pcall(function() return game:GetService("VirtualInputManager") end))
end

local function guiInset(obj)
    local sg = obj:FindFirstAncestorOfClass("ScreenGui")
    return (sg and not sg.IgnoreGuiInset) and GuiService:GetGuiInset() or Vector2.zero
end

local function clickReceiverOk(obj, cx, cy)
    if not CFG.SAFE_CLICK then return true end
    local sg = obj:FindFirstAncestorOfClass("ScreenGui")
    local pg = player:FindFirstChildOfClass("PlayerGui")
    if not (sg and pg) then return false end

    local inset = guiInset(obj)
    local screenX, screenY = cx + inset.X, cy + inset.Y
    local gi = GuiService:GetGuiInset()
    local ok, list = pcall(function()
        return pg:GetGuiObjectsAtPosition(screenX - gi.X, screenY - gi.Y)
    end)
    if not ok or type(list) ~= "table" then return true end

    for _, g in ipairs(list) do
        if g:IsA("GuiButton") or g.Active then
            return g:IsDescendantOf(sg)
        end
    end
    return false
end

local CLICK = {
    function(btn, obj, cx, cy)
        if not (getconnections and btn) then return false end
        local n = 0
        n = n + connFire(btn.MouseButton1Down, cx, cy)
        n = n + connFire(btn.MouseButton1Click)
        n = n + connFire(btn.MouseButton1Up, cx, cy)
        n = n + connFire(btn.Activated, fakeInput(cx, cy, Enum.UserInputState.End), 1)
        return n > 0
    end,
    function(btn, obj, cx, cy)
        if not (firesignal and btn) then return false end
        local any = false
        for _, sn in ipairs({"MouseButton1Down", "MouseButton1Click", "MouseButton1Up"}) do
            any = (pcall(function() firesignal(btn[sn]) end)) or any
        end
        local ok2 = pcall(function()
            firesignal(btn.Activated, fakeInput(cx, cy, Enum.UserInputState.End), 1)
        end)
        return any or ok2
    end,
    function(btn, obj, cx, cy)
        if not getconnections then return false end
        local list = {obj}
        if btn and btn ~= obj then list[#list + 1] = btn end
        local n = 0
        for _, t in ipairs(list) do
            n = n + connFire(t.InputBegan, fakeInput(cx, cy, Enum.UserInputState.Begin))
            n = n + connFire(t.InputEnded, fakeInput(cx, cy, Enum.UserInputState.End))
        end
        return n > 0
    end,
    function(btn, obj, cx, cy)
        if not hasVIM() then return false end
        local inset = guiInset(obj)
        return (pcall(function()
            local vim = game:GetService("VirtualInputManager")
            local x, y = cx + inset.X, cy + inset.Y
            pcall(function() vim:SendMouseMoveEvent(x, y, game) end)
            vim:SendMouseButtonEvent(x, y, 0, true, game, 0)
            task.wait(0.015)
            vim:SendMouseButtonEvent(x, y, 0, false, game, 0)
        end))
    end,
    function(btn, obj, cx, cy)
        if not hasVIM() then return false end
        local inset = guiInset(obj)
        return (pcall(function()
            local vim = game:GetService("VirtualInputManager")
            vim:SendTouchEvent(1, 0, cx + inset.X, cy + inset.Y)
            task.wait(0.015)
            vim:SendTouchEvent(1, 2, cx + inset.X, cy + inset.Y)
        end))
    end,
}

local ORDER = {1, 2, 4, 5, 3}

local function runClick(obj, idx)
    if not (obj and obj.Parent) then return false end
    local okB, btn = pcall(getButton, obj)
    if not okB then btn = nil end
    local okC, cx, cy = pcall(centerOf, obj)
    if not okC then return false end

    if idx == 4 or idx == 5 then
        local okG, safe = pcall(clickReceiverOk, obj, cx, cy)
        if okG and not safe then return false end
    end

    local ok, res = pcall(CLICK[idx], btn, obj, cx, cy)
    return ok and res and true or false
end

local function clickWith(obj, startPos)
    for i = 0, #ORDER - 1 do
        local pos = (startPos - 1 + i) % #ORDER + 1
        if runClick(obj, ORDER[pos]) then return pos end
    end
    return nil
end

-- =============================================
-- قراءة الكلمات
-- =============================================
local function norm(t)
    t = tostring(t or "")
    t = string.gsub(t, "<[^>]->", "")
    t = string.gsub(t, "%s+", "")
    t = string.gsub(t, "[\u{200B}-\u{200F}\u{FEFF}]", "")
    return string.upper(t)
end

local function wordKey(t)
    if #t > 60 then return nil end
    local k = norm(t)
    local n = #k
    if n < CFG.WORD_MIN or n > CFG.WORD_MAX then return nil end
    if string.match(k, "^%d+$") then return nil end
    if CFG.WORD_ASCII and not string.match(k, "^%w+$") then return nil end
    return k
end

local infoCache, infoCount = {}, 0
local function classify(t)
    local c = infoCache[t]
    if c ~= nil then return c end
    local res = false
    if #t <= 60 then
        if string.match(t, "%d+%s*/%s*%d+") and #t <= 16 then
            res = true
        else
            res = wordKey(t) or false
        end
    end
    infoCount = infoCount + 1
    if infoCount > 4000 then infoCache, infoCount = {}, 0 end
    infoCache[t] = res
    return res
end

local tracker = setmetatable({}, {__mode = "k"})

local function snapshot(now, src)
    local words, nw = {}, 0
    local cg = {}
    local gameOnly = gameGuiRef
    if gameOnly and not gameOnly.Parent then gameOnly = nil end
    for d in pairs(src) do
        if d.Parent then
            local t = d.Text
            if t ~= "" then
                local c = classify(t)
                if c and isShown(d) then
                    if c == true then
                        local sg = d:FindFirstAncestorOfClass("ScreenGui")
                        if sg then cg[sg] = (cg[sg] or 0) + 1 end
                    elseif (not gameOnly) or d:IsDescendantOf(gameOnly) then
                        local ap, as = d.AbsolutePosition, d.AbsoluteSize
                        local y = ap.Y + as.Y / 2
                        local rec = tracker[d]
                        if (not rec) or rec.key ~= c then
                            rec = {y0 = y, t0 = now, moved = false, key = c}
                            tracker[d] = rec
                        elseif math.abs(y - rec.y0) > 4 then
                            rec.moved = true
                        end
                        nw = nw + 1
                        words[nw] = {obj = d, key = c, y = y, rec = rec}
                    end
                end
            end
        else
            src[d] = nil
        end
    end
    local gui, gc = nil, 1
    for sg, n in pairs(cg) do
        if n > gc then gui, gc = sg, n end
    end
    return words, gui
end

local function findChoices(words, now)
    local rows = {}
    for _, w in ipairs(words) do
        if (not w.rec.moved) and now - w.rec.t0 > 0.2 then
            local row
            for _, r in ipairs(rows) do
                if math.abs(r.y - w.y) <= CFG.ROW_TOL then row = r; break end
            end
            if not row then
                row = {y = w.y, list = {}}
                rows[#rows + 1] = row
            end
            row.list[#row.list + 1] = w
        end
    end

    local best
    for _, r in ipairs(rows) do
        local seen, distinct = {}, 0
        for _, w in ipairs(r.list) do
            if not seen[w.key] then seen[w.key] = true; distinct = distinct + 1 end
        end
        if distinct >= 3 and ((not best) or r.y > best.y) then best = r end
    end
    if not best then return nil end

    local list = best.list
    if #list > 3 then
        local byParent, bestP, bestN = {}, nil, 0
        for _, it in ipairs(list) do
            local p = it.obj.Parent
            byParent[p] = (byParent[p] or 0) + 1
            if byParent[p] > bestN then bestP, bestN = p, byParent[p] end
        end
        local filtered = {}
        for _, it in ipairs(list) do
            if it.obj.Parent == bestP then filtered[#filtered + 1] = it end
        end
        if #filtered >= 3 then list = filtered end
    end

    local set = {y = best.y, objs = {}, keys = {}}
    for _, it in ipairs(list) do
        set.objs[it.obj] = it.key
        set.keys[it.key] = true
    end
    return set
end

local function choicesStillValid(set)
    if not set then return false end
    for obj, key in pairs(set.objs) do
        if not (obj.Parent and isShown(obj) and classify(obj.Text) == key) then
            return false
        end
    end
    return true
end

-- =============================================
-- حلقة الكلمات
-- =============================================
local preferred = 1

local function wordsLoop(tk)
    local choices, attempts = nil, {}
    local lastActive, failSince, lastIdle = 0, nil, 0
    local lastKeysTxt = ""

    local function dispatch(obj, a)
        a.busy = true
        task.spawn(function()
            local used = clickWith(obj, a.pos)
            if used then a.pos = used end
            a.busy = false
        end)
    end

    local function endGame()
        if W.active then
            W.active = false
            W.sessions = W.sessions + 1
            dbg("انتهت لعبة الكلمات")
        end
        gameGuiRef, gameSet = nil, {}
        choices, attempts, failSince = nil, {}, nil
    end

    while alive(tk) do
        local now = os.clock()

        if not W.active then
            if now - lastIdle >= CFG.IDLE_SCAN then
                lastIdle = now
                local _, gui = snapshot(now, texts)
                if gui then
                    W.active = true
                    lastActive = now
                    gameGuiRef = gui
                    gameSet = {}
                    for d in pairs(texts) do
                        if d:IsDescendantOf(gui) then gameSet[d] = true end
                    end
                    choices, attempts, failSince = nil, {}, nil
                    dbg("بدت لعبة الكلمات:", gui:GetFullName())
                end
            end
            task.wait(0.1)
        else
            RunService.Heartbeat:Wait()
            if not alive(tk) then break end
            now = os.clock()

            local src = gameSet
            if failSince and now - failSince > 2 and gameGuiRef and gameGuiRef.Parent then
                for d in pairs(texts) do
                    if d:IsDescendantOf(gameGuiRef) then gameSet[d] = true end
                end
            end
            local words, gui = snapshot(now, src)

            if gui then lastActive = now end
            if (not gui) and now - lastActive > CFG.END_AFTER then
                endGame()
            else
                if not choicesStillValid(choices) then
                    choices = findChoices(words, now)
                    if choices then
                        failSince = nil
                        attempts = {}
                        local ks = {}
                        for k in pairs(choices.keys) do ks[#ks + 1] = k end
                        table.sort(ks)
                        lastKeysTxt = table.concat(ks, "  ")
                        dbg("الكلمات الصحيحة:", lastKeysTxt)
                    else
                        failSince = failSince or now
                    end
                end

                if not choices then
                    setStatus("يقرأ الكلمات...")
                else
                    setStatus(lastKeysTxt)

                    local present = {}
                    for _, w in ipairs(words) do present[w.obj] = true end
                    for obj, a in pairs(attempts) do
                        if not present[obj] then
                            if a.n > 0 and a.y < choices.y - CFG.GROUND_MARGIN and preferred ~= a.pos then
                                preferred = a.pos
                                dbg("طريقة الضغط المعتمدة:", ORDER[a.pos])
                            end
                            attempts[obj] = nil
                        end
                    end

                    local matches = {}
                    for _, w in ipairs(words) do
                        if (not choices.objs[w.obj]) and choices.keys[w.key]
                            and gameGuiRef and w.obj:IsDescendantOf(gameGuiRef) then
                            local rec = w.rec
                            local fresh = now - rec.t0 < 0.3
                            local inRow = math.abs(w.y - choices.y) <= CFG.ROW_TOL
                            if (rec.moved or fresh) and (rec.moved or not inRow) then
                                matches[#matches + 1] = w
                            end
                        end
                    end
                    table.sort(matches, function(p, q) return p.y > q.y end)

                    local fired = 0
                    for _, w in ipairs(matches) do
                        local a = attempts[w.obj]
                        if not a then
                            a = {n = 0, t = -1, pos = preferred, y = w.y, busy = false}
                            attempts[w.obj] = a
                        end
                        a.y = w.y
                        if fired < CFG.MAX_PER_TICK and (not a.busy)
                            and a.n < CFG.MAX_ATTEMPTS
                            and (a.n == 0 or now - a.t >= CFG.RETRY_AFTER) then
                            if a.n > 0 then a.pos = a.pos % #ORDER + 1 end
                            a.n = a.n + 1
                            a.t = now
                            fired = fired + 1
                            dispatch(w.obj, a)
                        end
                    end
                end
            end
        end
    end
end

-- =============================================
-- نصوص التفريم: زر "خبير" + إشعار العبث
-- =============================================
local function scanTexts(baseline)
    local lvl, tamper, cur = nil, false, {}
    for d in pairs(texts) do
        if d.Parent then
            local t = d.Text
            if t ~= "" and #t < 160 then
                if (not lvl) and #t < 40 and string.find(t, CFG.LEVEL_TEXT, 1, true) and isShown(d) then
                    lvl = d
                end
                if string.find(t, CFG.TAMPER_TEXT, 1, true) and isShown(d) then
                    cur[d] = true
                    if baseline and not baseline[d] then tamper = true end
                end
            end
        end
    end
    return lvl, tamper, cur
end

-- =============================================
-- إشعارات نجاح الاختراق
-- =============================================
local function hasKeyword(t)
    for _, k in ipairs(CFG.SUCCESS_TEXTS) do
        if string.find(t, k, 1, true) then return true end
    end
    return false
end

local function snapNotes()
    local m = {}
    for d in pairs(texts) do
        if d.Parent then
            local t = d.Text
            if t ~= "" and #t < 200 and hasKeyword(t) and isShown(d) then
                m[d] = t
            end
        end
    end
    return m
end

local function scanSuccess(base)
    for d in pairs(texts) do
        if d.Parent then
            local t = d.Text
            if t ~= "" and #t < 200 and hasKeyword(t) and isShown(d) and base[d] ~= t then
                return true
            end
        end
    end
    return false
end

-- =============================================
-- إشعار تحويل الفلوس (كلمة "مقابل") — بدون إشعارات شراء الأداة
-- =============================================
local function hasWashKeyword(t)
    for _, ig in ipairs(CFG.WASH_IGNORE) do
        if string.find(t, ig, 1, true) then return false end
    end
    for _, k in ipairs(CFG.WASH_TEXTS) do
        if string.find(t, k, 1, true) then return true end
    end
    return false
end

local function snapWash()
    local m = {}
    for d in pairs(texts) do
        if d.Parent then
            local t = d.Text
            if t ~= "" and #t < 200 and hasWashKeyword(t) and isShown(d) then
                m[d] = t
            end
        end
    end
    return m
end

local function scanWash(base)
    for d in pairs(texts) do
        if d.Parent then
            local t = d.Text
            if t ~= "" and #t < 200 and hasWashKeyword(t) and isShown(d) and base[d] ~= t then
                return true
            end
        end
    end
    return false
end

local prefMenu = 1
local function smartClick(obj, verify, tk)
    for i = 0, #ORDER - 1 do
        if not alive(tk) then return false end
        local pos = (prefMenu - 1 + i) % #ORDER + 1
        if runClick(obj, ORDER[pos]) then
            if waitUntil(verify, CFG.CLICK_VERIFY, tk) then
                prefMenu = pos
                return true
            end
        end
    end
    return false
end

-- =============================================
-- محاولة صراف
-- =============================================
local function tryATMCore(pos, tk, idx)
    setStatus("يروح للصراف " .. toArabic(idx or ""))

    if workspace.StreamingEnabled then
        pcall(function() player:RequestStreamAroundAsync(pos, CFG.STREAM_TIMEOUT) end)
    end
    if not alive(tk) then return "stop" end

    teleport(pos)
    task.wait(0.5)
    if not alive(tk) then return "stop" end

    waitUntil(function() equipNow(); return toolInHand() ~= nil end, 4, tk)

    local _, _, baseline = scanTexts(nil)
    local firstPress, lastPress = nil, -100
    local searchStart = os.clock()
    local lvl = nil
    local hackSent, lvlSent = false, false

    while alive(tk) do
        local now = os.clock()
        if firstPress then
            if now - firstPress > CFG.ATM_TIMEOUT then return "timeout" end
        elseif now - searchStart > 7 then
            return "noprompt"
        end

        if not toolInHand() then equipNow() end

        local lv, tam = scanTexts(baseline)
        if firstPress and tam then return "tampered" end
        if firstPress and lv and now - firstPress >= CFG.MENU_DELAY then
            lvl = lv
            break
        end

        if firstPress and (not lv) and (not lvlSent) and now - firstPress > 2.5 then
            lvlSent = true
            dbg("القائمة ما طلعت، أرسل حزمة المستوى 3")
            fireGame(PKT_LVL3)
            return "done"
        end

        if (not firstPress) or ((not lv) and now - lastPress >= CFG.PRESS_INTERVAL) then
            local p = nearestPrompt()
            if p then
                setStatus("يضغط البرومبت (صراف " .. toArabic(idx or "") .. ")")
                pressPrompt(p)
                lastPress = os.clock()
                firstPress = firstPress or lastPress
            elseif (not firstPress) and (not hackSent) and now - searchStart > 2.5 then
                hackSent = true
                dbg("ما لقيت برومبت، أرسل حزمة الاختراق")
                fireGame(PKT_HACK)
                lastPress = os.clock()
                firstPress = lastPress
            end
        end
        task.wait(0.2)
    end
    if not alive(tk) then return "stop" end

    setStatus("يختار خبير")
    task.wait(CFG.EXPERT_DELAY)
    if not alive(tk) then return "stop" end
    local l2 = scanTexts(nil) or lvl
    local okLvl = l2 and smartClick(l2, function()
        return not (l2.Parent and isShown(l2))
    end, tk)
    if not okLvl and alive(tk) then
        dbg("قائمة الصعوبة ما سكّرت، أرسل حزمة المستوى 3")
        fireGame(PKT_LVL3)
    end
    if not alive(tk) then return "stop" end
    return "done"
end

local function tryATM(pos, tk, idx)
    local ok, res = pcall(tryATMCore, pos, tk, idx)
    if not ok then
        dbg("خطأ صراف:", res)
        return "error"
    end
    return res
end

-- =============================================
-- ينتظر نهاية اللعبة + إشعار النجاح
-- =============================================
local function waitGameResult(tk, base, startWait)
    startWait = startWait or CFG.GAME_START_WAIT
    local s0, t0 = W.sessions, os.clock()
    local endedAt = nil
    local success = false
    setStatus("ينتظر اللعبة...")
    while alive(tk) and os.clock() - t0 < CFG.GAME_MAX_WAIT do
        if scanSuccess(base) then
            success = true
            break
        end
        local now = os.clock()
        if W.sessions > s0 and not endedAt then
            endedAt = now
            setStatus("ينتظر إشعار الاختراق...")
        end
        if endedAt and now - endedAt > CFG.RESULT_WAIT then break end
        if (not W.active) and (not endedAt) and now - t0 > startWait then break end
        task.wait(0.15)
    end
    return success, endedAt ~= nil
end

-- =============================================
-- ensureTool: يشتري عند مكان الشراء لو الأداة مو معه قبل الصراف
-- (الغسيل خلص، فالشراء مسموح هنا قبل الصراف فقط)
-- وضع تغيير السيرفر: هذا هو المكان الوحيد اللي يشتري فيه (بالسيرفر الجديد)
-- =============================================
local function ensureTool(tk)
    if not hasTool() then
        WM.buyLock = false   -- الغسيل خلص، الشراء مسموح قبل الصراف فقط
        setStatus("يروح لمكان شراء الأداة...")
        teleport(CFG.POS_BUY)
        task.wait(0.35)
        setStatus("يشتري الأداة...")
        local tries = 0
        while alive(tk) and not hasTool() and tries < 8 do
            local hrp = getHRP()
            if hrp and (hrp.Position - CFG.POS_BUY).Magnitude > CFG.WASH_NEAR_START then
                teleport(CFG.POS_BUY)
                task.wait(0.3)
            end
            fireGame(PKT_BUY)
            tries = tries + 1
            waitUntil(hasTool, 2, tk)
        end
    end
    if not alive(tk) then return false end

    setStatus("يمسك الأداة")
    waitUntil(function() equipNow(); return toolInHand() ~= nil end, 6, tk)
    return toolInHand() ~= nil
end

-- =============================================
-- تحويل الفلوس — كل شي داخل الجدول WM
-- القاعدة: التحويل ما يُعتبر تم إلا بدليل حقيقي:
--   (أ) إشعار جديد فيه "مقابل" (بدون إشعارات شراء الأداة) ظهر بعد أول ضغطة
--   (ب) أو رقم البرومبت نزل / صار صفر
--   (ج) أو (لو ما فيه برومبت وفيه زر شاشة) الزر اختفى بعد الضغط
-- بعد الدليل يكمل WASH_CONFIRM ثواني للتأكيد، وأقصى انتظار عند البرومبت WASH_STAY (10).
-- أول ما ينتأكد الغسيل: يوقف الضغط ويعطّل البرومبت (عشان ما ينضغط لو تحول لشراء أداة).
-- طول وقت الغسيل: حزمة شراء الأداة مقفولة (WM.buyLock).
-- v38:
--   * زر "بدأ التفريم": بعد الغسيل ينتقل لمكان الشراء، يشتري الأداة، ثم يروح مكان الانتظار.
--   * زر "تغيير السيرفر": بعد الغسيل ما يشتري أبداً، يروح مكان الانتظار ويغير السيرفر،
--     والأداة تنشترى بالسيرفر الجديد قبل أول صراف.
-- v39:
--   * ما نعطّل إلا البرومبتات اللي نصها شراء أداة (مو أي برومبت قريب)
--   * بحث البرومبت: النص > الاسم (بدون برومبتات الشراء) > أي برومبت قريب مو شراء
-- =============================================
function WM.number(p)
    local s = tostring(p.ActionText) .. " " .. tostring(p.ObjectText)
    local n = string.match(s, "%d[%d,]*")
    if not n then return nil end
    return tonumber((string.gsub(n, ",", "")))
end

-- هل البرومبت صار نصه شراء أداة (مو برومبت غسيل)؟
function WM.isBuyPrompt(p)
    if isWashPrompt(p) then return false end
    local txt = tostring(p.ActionText) .. " " .. tostring(p.ObjectText)
    for _, k in ipairs(CFG.BUY_PROMPT_TEXTS) do
        if string.find(txt, k, 1, true) then return true end
    end
    return false
end

function WM.isNamed(p)
    for _, n in ipairs(CFG.WASH_PROMPT_NAMES) do
        if p.Name == n then return true end
    end
    return false
end

-- allowNear: يسمح بالاحتياط (أي برومبت قريب مو نصه شراء)
function WM.findPrompt(allowNear)
    local hrp = getHRP()
    local origin = hrp and hrp.Position or CFG.POS_START
    local bestTxt, bestTxtD = nil, CFG.WASH_PROMPT_RANGE
    local bestName, bnd = nil, CFG.WASH_PROMPT_NEAR
    local bestNear, nnd = nil, CFG.WASH_FALLBACK_RANGE
    for p in pairs(prompts) do
        if p.Parent and p.Enabled then
            local pos = promptPos(p)
            if pos then
                local d = (pos - origin).Magnitude
                if d < CFG.WASH_PROMPT_RANGE then
                    if isWashPrompt(p) then
                        if d < bestTxtD then bestTxt, bestTxtD = p, d end
                    elseif not WM.isBuyPrompt(p) then
                        if WM.isNamed(p) and d < bnd then
                            bestName, bnd = p, d
                        elseif allowNear and d < nnd then
                            bestNear, nnd = p, d
                        end
                    end
                end
            end
        end
    end
    return bestTxt or bestName or bestNear
end

-- يطبع كل البرومبتات القريبة (للتشخيص لو ما لقى برومبت غسيل)
function WM.dump()
    local hrp = getHRP()
    local origin = hrp and hrp.Position or CFG.POS_START
    local n = 0
    for p in pairs(prompts) do
        if p.Parent then
            local pos = promptPos(p)
            if pos then
                local d = (pos - origin).Magnitude
                if d <= CFG.WASH_DUMP_RANGE then
                    n = n + 1
                    dbg("برومبت قريب:", p.Name,
                        "| فعل:", tostring(p.ActionText),
                        "| كائن:", tostring(p.ObjectText),
                        "| مفعّل:", tostring(p.Enabled),
                        "| بُعد:", math.floor(d))
                end
            end
        end
    end
    if n == 0 then dbg("ما فيه أي برومبت قريب (يمكن الماب ما تحمّلت)") end
end

function WM.lock(p)
    if WM.hp == p and WM.hc then return end
    if WM.hc then pcall(function() WM.hc:Disconnect() end); WM.hc = nil end
    WM.hp = p
    makeInstant(p)
    pcall(function()
        WM.hc = p:GetPropertyChangedSignal("HoldDuration"):Connect(function()
            if p.HoldDuration ~= 0 then p.HoldDuration = 0 end
        end)
    end)
end

function WM.unlock()
    if WM.hc then pcall(function() WM.hc:Disconnect() end) end
    WM.hc, WM.hp = nil, nil
end

function WM.unfreeze()
    if WM.fc then
        pcall(function() WM.fc:Disconnect() end)
        WM.fc = nil
    end
end

function WM.freeze(pos)
    WM.unfreeze()
    WM.fc = RunService.Heartbeat:Connect(function()
        if not running then
            WM.unfreeze()
            return
        end
        local hrp = getHRP()
        if hrp then
            pcall(function()
                hrp.AssemblyLinearVelocity = Vector3.zero
                hrp.CFrame = CFrame.new(pos)
            end)
        end
    end)
end

function WM.findLabel()
    for d in pairs(texts) do
        if d.Parent then
            local t = d.Text
            if t ~= "" and #t < 80 and isShown(d) then
                for _, k in ipairs(CFG.WASH_PROMPT_TEXTS) do
                    if string.find(t, k, 1, true) then return d end
                end
            end
        end
    end
    return nil
end

function WM.labelButton(lbl)
    if lbl:IsA("GuiButton") then return lbl end
    local lx, ly = centerOf(lbl)
    local lc = Vector2.new(lx, ly)
    local o = lbl
    for _ = 1, 5 do
        o = o and o.Parent
        if (not o) or o:IsA("PlayerGui") then break end
        local best, bd = nil, math.huge
        for _, d in ipairs(o:GetDescendants()) do
            if d:IsA("GuiButton") and isShown(d) and not (myGui and d:IsDescendantOf(myGui)) then
                local dx, dy = centerOf(d)
                local dist = (Vector2.new(dx, dy) - lc).Magnitude
                if dist < bd and dist <= CFG.WASH_BTN_MAX_DIST then best, bd = d, dist end
            end
        end
        if best then return best end
        if o:IsA("ScreenGui") then break end
    end
    return nil
end

-- الضغط على برومبت الغسيل (يتوقف فوراً أول ما ينتأكد الغسيل، حتى الضغطات المعلّقة)
function WM.press(p)
    if WM.washDone then return end
    WM.lock(p)
    task.spawn(function()
        if WM.washDone then return end
        if fireproximityprompt then
            pcall(fireproximityprompt, p)
            if WM.washDone then return end
            task.wait(0.05)
            if WM.washDone then return end
            pcall(fireproximityprompt, p)
        end
        if WM.washDone then return end
        pcall(function()
            p:InputHoldBegin()
            task.wait(0.05)
            p:InputHoldEnd()
        end)
    end)
end

-- أثناء الغسيل: يعطّل برومبتات الشراء القريبة فقط (اللي نصها شراء أداة) عشان ما ينضغط شي غلط
-- (v39: ما نعطّل أي برومبت ثاني، عشان ما نعطّل برومبت الغسيل نفسه لو نصه لسا ما انقرأ)
function WM.disableOthers(center, radius)
    for p in pairs(prompts) do
        if p.Parent and p.Enabled and (not isWashPrompt(p)) and (not WM.isNamed(p)) and WM.isBuyPrompt(p) then
            local pos = promptPos(p)
            if pos and (pos - center).Magnitude <= radius then
                WM.dis[#WM.dis + 1] = p
                pcall(function() p.Enabled = false end)
            end
        end
    end
end

function WM.restoreOthers()
    for _, p in ipairs(WM.dis) do
        pcall(function() if p.Parent then p.Enabled = true end end)
    end
    WM.dis = {}
end

function WM.streamHere(pos)
    if workspace.StreamingEnabled then
        task.spawn(function()
            pcall(function() player:RequestStreamAroundAsync(pos, CFG.STREAM_TIMEOUT) end)
        end)
    end
end

-- محاولة واحدة. ترجّع: "ok" (انتأكد) / "none" (ما فيه فلوس للتحويل) / "fail" / "stop"
function WM.attempt(tk)
    -- أي برومبت عطّلناه قبل (محاولة سابقة) نرجّعه أول شي
    WM.restoreOthers()

    setStatus("يروح لمكان تحويل الفلوس...")
    WM.streamHere(CFG.POS_START)
    task.wait(0.15)
    if not alive(tk) then return "stop" end
    teleport(CFG.POS_START)
    task.wait(CFG.WASH_TP_WAIT)
    local t0 = os.clock()

    -- 1) يدور على البرومبت / زر الشاشة
    setStatus("يدور على زر التحويل...")
    local p, lbl = nil, nil
    local lastScan = -10
    local dumped = false
    while alive(tk) and os.clock() - t0 < CFG.WASH_FIND do
        local now = os.clock()
        if now - lastScan >= 1.5 then
            lastScan = now
            task.spawn(rescanPrompts)
            WM.disableOthers(CFG.POS_START, 120)
            WM.streamHere(CFG.POS_START)
            local hrp = getHRP()
            if hrp and (hrp.Position - CFG.POS_START).Magnitude > CFG.WASH_NEAR_START then
                teleport(CFG.POS_START)
            end
        end
        p = WM.findPrompt(now - t0 > CFG.WASH_FIND / 2)
        lbl = WM.findLabel()
        if p or lbl then break end
        if (not dumped) and now - t0 > 3 then
            dumped = true
            WM.dump()
        end
        task.wait(0.2)
    end
    if not alive(tk) then return "stop" end
    if (not p) and (not lbl) then
        dbg("التحويل: ما لقيت برومبت ولا زر غسل طول", CFG.WASH_FIND, "ثواني")
        if not dumped then WM.dump() end
        return "none"
    end
    if p then
        dbg("التحويل: لقى برومبت:", p.Name, "|", tostring(p.ActionText), "|", tostring(p.ObjectText))
    end

    local startNum = p and WM.number(p) or nil
    local hadLabel = lbl ~= nil

    if startNum == 0 then
        local z0 = os.clock()
        while alive(tk) and os.clock() - z0 < 3 do
            task.wait(0.3)
            local n = (p.Parent and WM.number(p)) or nil
            if n ~= 0 then startNum = n; break end
        end
        if not alive(tk) then return "stop" end
        if startNum == 0 then
            dbg("التحويل: الفلوس صفر")
            return "none"
        end
    end

    -- 2) انتقال واحد لمكان البرومبت + تثبيت
    local anchor = nil
    if p then
        local pos = promptPos(p)
        if pos then
            anchor = pos
            setStatus("يقرّب من زر التحويل...")
            teleport(anchor)
        end
    end
    if not anchor then
        local hrp = getHRP()
        anchor = hrp and hrp.Position or CFG.POS_START
    end
    setNoclip(true)
    WM.freeze(anchor)
    task.wait(0.4)
    if not alive(tk) then WM.unfreeze(); return "stop" end

    WM.washDone = false
    local arrive = os.clock()
    local base = snapWash()
    local pressed, verifiedAt, reason = false, nil, nil
    local loopN = 0
    local toolAtStart, warned = hasTool(), false

    -- 3) يضغط ويتأكد (أقصى مدة = WASH_STAY)
    while alive(tk) do
        local now = os.clock()
        local elapsed = now - arrive
        loopN = loopN + 1

        if (not toolAtStart) and (not warned) and hasTool() then
            warned = true
            dbg("⚠ الأداة وصلت وقت الغسيل من مصدر ثاني (مو من حزمة السكربت)")
        end

        if elapsed >= CFG.WASH_STAY then break end
        if verifiedAt and now - verifiedAt >= CFG.WASH_CONFIRM then break end

        local hrp = getHRP()
        if hrp and (hrp.Position - anchor).Magnitude > CFG.WASH_ANCHOR_TOL then
            dbg("التحويل: ابتعد عن البرومبت، يرجعه")
            teleport(anchor)
            task.wait(0.15)
        end

        -- البرومبت اختفى أو صار نصه شراء أداة: يدور على برومبت غسيل ثاني
        if (not verifiedAt) and ((not (p and p.Parent)) or WM.isBuyPrompt(p)) then
            local np = WM.findPrompt(true)
            if np and np ~= p then
                p = np
                dbg("التحويل: غيّر البرومبت إلى:", p.Name, "|", tostring(p.ActionText), "|", tostring(p.ObjectText))
                local pos = promptPos(np)
                if pos and (pos - anchor).Magnitude > CFG.WASH_ANCHOR_TOL then
                    anchor = pos
                    teleport(anchor)
                    WM.freeze(anchor)
                end
            end
        end

        if not pressed then
            base = snapWash()
        end

        -- بعد ما ينتأكد الغسيل ما يضغط شي، وما يضغط أي برومبت نصه شراء أداة
        local pressedThisLoop = false
        if (not verifiedAt) and p and p.Parent and p.Enabled then
            if WM.isBuyPrompt(p) then
                dbg("⛔ البرومبت صار شراء أداة، ما يضغطه")
            else
                WM.press(p)
                pressedThisLoop = true
            end
        end

        local l = (not verifiedAt) and WM.findLabel() or nil
        if l then
            hadLabel = true
            local b = WM.labelButton(l)
            if b then
                clickWith(b, (loopN - 1) % #ORDER + 1)
                pressedThisLoop = true
            end
        end
        if pressedThisLoop then pressed = true end

        setStatus("يحول الفلوس... " .. toArabic(math.floor(elapsed)) .. "/" .. toArabic(CFG.WASH_STAY))

        task.wait(CFG.WASH_PRESS_GAP)

        if pressed and not verifiedAt then
            if scanWash(base) then
                verifiedAt, reason = os.clock(), "إشعار"
            elseif p and p.Parent and p.Enabled then
                local n = WM.number(p)
                if n == 0 or (n and startNum and n < startNum) then
                    verifiedAt, reason = os.clock(), "نزل الرقم"
                end
            elseif (not p) and hadLabel and (not WM.findLabel()) then
                verifiedAt, reason = os.clock(), "اختفى الزر"
            end
            if verifiedAt then
                -- أول ما ينتأكد: يوقف الضغط فوراً (حتى الضغطات المعلّقة)
                WM.washDone = true
                WM.unlock()
                dbg("التحويل: دليل =", reason, "| يكمل للتأكيد")
                -- ينتأكد الغسيل: يعطّل البرومبت عشان ما ينضغط بالغلط (يرجع بعد ما يبتعد)
                if p and p.Parent and p.Enabled then
                    WM.dis[#WM.dis + 1] = p
                    pcall(function() p.Enabled = false end)
                end
            end
        end
    end

    WM.unfreeze()
    if not alive(tk) then return "stop" end
    if verifiedAt then
        dbg("التحويل: انتأكد ✔")
        return "ok"
    end
    dbg("التحويل: ما انتأكد بعد", CFG.WASH_STAY, "ثواني")
    if not pressed then WM.dump() end
    return "fail"
end

-- شراء الأداة بعد الغسيل (زر بدأ التفريم فقط):
-- ينتقل لمكان الشراء، يرجّع حزمة الشراء، ويشتري (ويرجعه لو ابتعد)
function WM.buy(tk)
    setStatus("يروح لمكان شراء الأداة...")
    WM.restoreOthers()
    teleport(CFG.POS_BUY)
    task.wait(0.3)

    -- الغسيل خلص: نفتح قفل حزمة الشراء
    WM.buyLock = false
    dbg("الشراء: انفتحت حزمة شراء الأداة")

    if hasTool() then return true end
    setStatus("يشتري الأداة...")
    local t0 = os.clock()
    local lastFire = -10
    while alive(tk) and (not hasTool()) and os.clock() - t0 < CFG.WASH_BUY_TIMEOUT do
        local hrp = getHRP()
        if hrp and (hrp.Position - CFG.POS_BUY).Magnitude > CFG.WASH_NEAR_START then
            dbg("الشراء: ابتعد عن مكان الشراء، يرجعه")
            teleport(CFG.POS_BUY)
            task.wait(0.3)
        end
        if os.clock() - lastFire >= 0.8 then
            lastFire = os.clock()
            fireGame(PKT_BUY)
        end
        task.wait(0.1)
    end
    local got = hasTool()
    if not got then dbg("الشراء: ما انشترت الأداة، بيحاول عند الصراف") end
    return got
end

-- جولة غسيل: ترجّع true لو انتهى (تم أو ما فيه فلوس)، false لو لازم يعيد
function WM.run(tk)
    STATE.phase = "wash"
    touch()
    setNoclip(false)

    -- قفل حزمة شراء الأداة طول فترة الغسيل
    WM.buyLock = true
    dbg("الغسيل: انقفلت حزمة شراء الأداة")

    local result = "fail"
    for attempt = 1, CFG.WASH_RETRIES do
        if not alive(tk) then break end
        result = WM.attempt(tk)
        WM.unfreeze()
        WM.unlock()
        dbg("التحويل: محاولة", attempt, "=>", result)
        -- سرق فلوس قبل شوي وما لقى برومبت؟ غالباً الماب/البرومبت لسا ما تحمّل، يعيد المحاولة
        if result == "none" and STATE.stole and attempt < 2 then
            dbg("التحويل: ما لقيت البرومبت مع إن فيه فلوس مسروقة، يعيد")
            result = "fail"
        end
        if result ~= "fail" then break end
        setStatus("ما انتأكد التحويل، يعيد...")
        task.wait(0.8)
    end
    WM.unfreeze()
    WM.unlock()
    touch()

    if (not alive(tk)) or result == "stop" then
        WM.buyLock = false
        WM.restoreOthers()
        return false
    end
    if result == "fail" then
        WM.buyLock = false
        WM.restoreOthers()
        return false
    end

    STATE.needWash = false
    STATE.stole = false

    if alive(tk) then
        if HOP.on then
            -- وضع تغيير السيرفر: ما يشتري الأداة بعد الغسيل أبداً (قفل الشراء يبقى)
            -- الأداة تنشترى بالسيرفر الجديد قبل أول صراف (ensureTool)
            dbg("وضع تغيير السيرفر: ما يشتري الأداة بعد الغسيل")
        else
            -- زر بدأ التفريم: يشتري الأداة ثم يروح مكان الانتظار
            WM.buy(tk)
            WM.buyLock = false
            task.wait(CFG.WASH_AFTER)
        end
    end
    if alive(tk) then
        setStatus("يروح لمكان الانتظار...")
        teleport(CFG.POS_WAIT)
        task.wait(0.3)
    end
    WM.restoreOthers()   -- ترجع البرومبتات بعد ما يبتعد عنها
    return true
end

-- يعيد جولات الغسيل لين يتأكد (أو تخلص الجولات)
function WM.washLoop(tk)
    local rounds = 0
    while STATE.needWash and alive(tk) and rounds < CFG.WASH_ROUNDS do
        rounds = rounds + 1
        if WM.run(tk) then return true end
        if not alive(tk) then return false end
        dbg("الغسيل: جولة", rounds, "ما نجحت، يعيد")
        task.wait(1)
    end
    return not STATE.needWash
end

-- =============================================
-- صراف واحد مع إعادة المحاولة
-- =============================================
local function doATM(i, pos, tk)
    local resume = STATE.stage == "game" and STATE.atmIdx == i
        and os.time() - (STATE.gameStart or 0) < CFG.GAME_MAX_WAIT
    local tries = 0

    while alive(tk) and tries < CFG.ATM_RETRIES do
        local res

        if resume then
            resume = false
            res = "resume"
            dbg("الصراف", i, "يكمل لعبة شغالة")
        else
            tries = tries + 1
            STATE.stage = "press"
            touch()
            if not ensureTool(tk) then
                if not alive(tk) then return "stop" end
                dbg("الأداة مو معي، يعيد المحاولة", i)
                task.wait(1)
                res = "notool"
            else
                res = tryATM(pos, tk, i)
            end
        end

        if res == "stop" or not alive(tk) then return "stop" end
        if res == "tampered" then
            STATE.stage = nil
            return "skip"
        end

        if res == "done" or res == "resume" then
            if res == "done" then
                STATE.stage = "game"
                STATE.gameStart = os.time()
                touch()
            end
            local base = snapNotes()
            local success, ended = waitGameResult(tk, base,
                res == "resume" and CFG.RESUME_GAME_WAIT or nil)
            if not alive(tk) then return "stop" end

            if success or (ended and CFG.COUNT_ENDED_AS_SUCCESS) then
                STATE.stage = nil
                return "success"
            end
            dbg("الصراف", i, "فشلت السرقة، يعيد نفس الصراف", tries, "/", CFG.ATM_RETRIES)
            STATE.stage = nil
        elseif res ~= "notool" then
            dbg("الصراف", i, "=>", res, "يعيد المحاولة")
            task.wait(0.5)
        end
    end

    STATE.stage = nil
    return "fail"
end

-- =============================================
-- جاهزية الصرافات + الانتظار
-- =============================================
local function getATMs()
    return {CFG.POS_HACK, CFG.POS_ATM2, CFG.POS_ATM3, CFG.POS_ATM4 + CFG.ATM4_LIFT}
end

local function atmReady(i, atms, now)
    if STATE.stage == "game" and STATE.atmIdx == i then return true end
    local c = STATE.closed[i] or 0
    if now >= c then return true end
    if CFG.DETECT_OPEN
        and STATE.block[i] ~= c
        and (c - now) <= (CFG.ATM_COOLDOWN - CFG.DETECT_MIN_AGE)
        and atmPromptOpen(atms[i]) then
        dbg("الصراف", i, "انفتح (كشف بدري)")
        return true
    end
    return false
end

-- ينتظر لين صرافة تنفك (الأداة اشتراها بعد الغسيل)
-- وضع تغيير السيرفر: يتجاهل أي صرافة ترسبنت ويغير السيرفر بعد ما يخلص الغسيل بشوي
local function waitForATM(tk, atms)
    STATE.phase = "wait"
    touch()

    setNoclip(false)
    -- وضع تغيير السيرفر: ينتظر شوي بعد الغسيل قبل ما يغير
    if HOP.on then task.wait(CFG.HOP_AFTER_WASH) end
    if HOP.on then
        setStatus("تغيير السيرفر...")
    else
        setStatus("يروح لمكان الانتظار...")
    end
    local hrp0 = getHRP()
    if (not hrp0) or (hrp0.Position - CFG.POS_WAIT).Magnitude > 15 then
        teleport(CFG.POS_WAIT)
        task.wait(0.4)
    end

    while alive(tk) do
        local now = os.time()
        if not HOP.on then
            for i = 1, #atms do
                if atmReady(i, atms, now) then
                    setNoclip(true)
                    return
                end
            end
        end

        local hrp = getHRP()
        if hrp and (hrp.Position.Y < CFG.POS_WAIT.Y - 40
            or (hrp.Position - CFG.POS_WAIT).Magnitude > 150) then
            teleport(CFG.POS_WAIT)
        end

        -- وهو بمكان الانتظار: يغير السيرفر (لو الوضع مفعّل)
        if HOP.on and (not HOP.busy) and os.clock() - HOP.lastTry >= CFG.HOP_RETRY then
            HOP.lastTry = os.clock()
            HOP.go(tk)
        end

        if HOP.on then
            setStatus("تغيير السيرفر...")
        else
            setStatus("انتظار صرافة تنفك...")
        end
        task.wait(CFG.WAIT_POLL)
    end
end

-- =============================================
-- دورة التفريم
-- أول مرة: يمر على الأربع صرافات، وبعدها يغسل مرة وحدة (سواء سرق منها أو لا)
-- بعدها: كل صرافة ينجح بسرقتها يغسل بعدها علطول
-- =============================================
local function runCycle(tk)
    local atms = getATMs()

    -- لو انقطع وسط الغسيل (تغيير سيرفر / إعادة تشغيل) يكمل الغسيل أول شي
    local resumeWash = (STATE.phase == "wash") and STATE.needWash
    STATE.phase = "atm"
    touch()

    if resumeWash then
        dbg("يكمل الغسيل اللي انقطع")
        WM.washLoop(tk)
        if not alive(tk) then return end
        STATE.phase = "atm"
        touch()
    end

    -- احتياط: لو صار خطأ وقت الغسيل وبقي القفل، نفتحه
    WM.buyLock = false

    -- دخل سيرفر مزدحم بتغيير السيرفر: ما يفرّم، يغيّر علطول لسيرفر أفضى
    if HOP.on and HOP.crowded then
        dbg("السيرفر مزدحم، يغيّر علطول بدون تفريم")
        waitForATM(tk, atms)
        HOP.crowded = false
        return
    end

    for i = 1, #atms do
        if not alive(tk) then return end

        if atmReady(i, atms, os.time()) then
            if not WM.sweepDone then STATE.needWash = true end
            STATE.atmIdx = i
            touch()

            local r = doATM(i, atms[i], tk)
            dbg("الصراف", i, "=>", r)
            if r == "stop" or not alive(tk) then return end

            local now = os.time()
            if r == "success" then
                STATE.closed[i] = now + CFG.ATM_COOLDOWN
                STATE.needWash = true
                STATE.stole = true
                dbg("الصراف", i, "اكتمل")
            elseif r == "skip" then
                STATE.closed[i] = now + CFG.ATM_COOLDOWN
                STATE.block[i] = STATE.closed[i]
            else
                STATE.closed[i] = now + CFG.ATM_FAIL_RETRY
                STATE.block[i] = STATE.closed[i]
            end
            touch()

            -- بعد الجولة الأولى: يغسل علطول بعد كل صرافة
            if WM.sweepDone and STATE.needWash then
                WM.washLoop(tk)
                if not alive(tk) then return end
            end
        end
    end

    STATE.stage = nil
    STATE.atmIdx = nil
    if not alive(tk) then return end

    WM.sweepDone = true

    -- نهاية الجولة الأولى (أو أي فلوس باقية): يغسل
    if STATE.needWash then
        WM.washLoop(tk)
        if not alive(tk) then return end
    end

    waitForATM(tk, atms)
end

-- =============================================
-- Anti-AFK
-- =============================================
local antiAfkConn, antiAfkId = nil, 0

local function stopAntiAFK()
    antiAfkId = antiAfkId + 1
    if antiAfkConn then
        pcall(function() antiAfkConn:Disconnect() end)
        antiAfkConn = nil
    end
end

local function startAntiAFK()
    stopAntiAFK()
    local id = antiAfkId
    local okVU, VU = pcall(function() return game:GetService("VirtualUser") end)
    if not okVU then VU = nil end

    local function ping()
        if VU then
            pcall(function()
                VU:CaptureController()
                VU:ClickButton2(Vector2.new(0, 0))
            end)
        end
        pcall(function()
            local vim = game:GetService("VirtualInputManager")
            vim:SendKeyEvent(true, Enum.KeyCode.LeftShift, false, game)
            task.wait(0.05)
            vim:SendKeyEvent(false, Enum.KeyCode.LeftShift, false, game)
        end)
    end

    antiAfkConn = player.Idled:Connect(function()
        dbg("Anti-AFK: Idled")
        ping()
    end)

    task.spawn(function()
        while antiAfkId == id do
            for _ = 1, 60 do
                if antiAfkId ~= id then return end
                task.wait(1)
            end
            ping()
        end
    end)
end

local function startAll()
    if running then return end
    running = true
    token = token + 1
    local tk = token
    W.active = false
    WM.sweepDone = false
    WM.buyLock = false
    WM.washDone = false
    WM.installHook()
    ensureRegistry()
    FZ.start()
    setNoclip(true)
    startPromptTracking()
    startKeepTool()
    startAntiAFK()
    task.spawn(function()
        local ok, err = pcall(wordsLoop, tk)
        if not ok then dbg("خطأ كلمات:", err) end
    end)
    task.spawn(function()
        while alive(tk) do
            local ok, err = pcall(runCycle, tk)
            if not ok then
                dbg("خطأ:", err)
                WM.buyLock = false
                task.wait(1)
            end
            task.wait(0.2)
        end
    end)
end

local setVisual = function() end

stopAll = function()
    running = false
    token = token + 1
    W.active = false
    HOP.on = false
    HOP.busy = false
    HOP.crowded = false
    WM.buyLock = false
    WM.restoreOthers()
    WM.unfreeze()
    WM.unlock()
    FZ.stop()
    setNoclip(false)
    clearKeep()
    stopAntiAFK()
    stopPromptTracking()
    stopRegistry()
    setStatus("مطفي", true)
    pcall(setVisual, false)
end

-- =============================================
-- الواجهة
-- =============================================
do
    local gui = Instance.new("ScreenGui")
    gui.Name = "M7_Bar"
    gui.ResetOnSpawn = false
    gui.IgnoreGuiInset = true
    gui.DisplayOrder = 998
    gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    if not pcall(function() gui.Parent = game:GetService("CoreGui") end) then
        gui.Parent = player:WaitForChild("PlayerGui")
    end
    myGui = gui

    local GRAY = Color3.fromRGB(140, 140, 148)
    local BTN_BG = Color3.fromRGB(32, 32, 38)

    local clickSound = Instance.new("Sound")
    clickSound.SoundId = "rbxassetid://6895079853"
    clickSound.Volume = 0.7
    clickSound.Parent = gui

    local clickDebounce = false
    local function playClick()
        if clickDebounce then return end
        clickDebounce = true
        pcall(function() clickSound:Play() end)
        task.delay(0.08, function() clickDebounce = false end)
    end

    local function addStroke(obj, th)
        local s = Instance.new("UIStroke")
        s.Color = GRAY
        s.Thickness = th or 0.6
        s.Transparency = 0.45
        s.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
        s.Parent = obj
        return s
    end

    local function isPointer(i)
        return i.UserInputType == Enum.UserInputType.MouseButton1
            or i.UserInputType == Enum.UserInputType.Touch
    end

    local function pressFX(btn, target)
        target = target or btn
        local sc = Instance.new("UIScale")
        sc.Parent = target
        local st = target:FindFirstChildOfClass("UIStroke")
        local function down()
            TweenService:Create(sc, TweenInfo.new(0.1, Enum.EasingStyle.Quad), {Scale = 0.92}):Play()
            if st then TweenService:Create(st, TweenInfo.new(0.1), {Thickness = 1.5}):Play() end
        end
        local function up()
            TweenService:Create(sc, TweenInfo.new(0.2, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {Scale = 1}):Play()
            if st then TweenService:Create(st, TweenInfo.new(0.15), {Thickness = 0.6}):Play() end
        end
        btn.InputBegan:Connect(function(i) if isPointer(i) then down() end end)
        btn.InputEnded:Connect(function(i) if isPointer(i) then up() end end)
        btn.MouseLeave:Connect(up)
        if UIS.MouseEnabled then
            btn.MouseEnter:Connect(function()
                TweenService:Create(sc, TweenInfo.new(0.12), {Scale = 1.06}):Play()
            end)
        end
        return sc
    end

    local DRAG_THRESHOLD = 6

    local function setupSmoothDrag(inputFrame, moveFrame, onMoved)
        moveFrame = moveFrame or inputFrame
        local dragging = false
        local dragStart = nil
        local startPos = nil
        local moved = false

        inputFrame.InputBegan:Connect(function(input)
            if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
                dragging = true
                moved = false
                dragStart = input.Position
                startPos = moveFrame.Position

                local endedConn
                endedConn = input.Changed:Connect(function()
                    if input.UserInputState == Enum.UserInputState.End then
                        dragging = false
                        if endedConn then
                            endedConn:Disconnect()
                        end
                    end
                end)
            end
        end)

        inputFrame.InputChanged:Connect(function(input)
            if not dragging or not dragStart then return end
            if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
                local delta = input.Position - dragStart
                if moved or math.abs(delta.X) > DRAG_THRESHOLD or math.abs(delta.Y) > DRAG_THRESHOLD then
                    moved = true
                    moveFrame.Position = UDim2.new(
                        startPos.X.Scale, startPos.X.Offset + delta.X,
                        startPos.Y.Scale, startPos.Y.Offset + delta.Y
                    )
                    if onMoved then onMoved(moveFrame.Position) end
                end
            end
        end)

        return {
            wasMoved = function() return moved end
        }
    end

    local MAIN_DEFAULT = UDim2.new(0, 12, 0.5, -60)
    local M7_DEFAULT   = UDim2.new(0, 35, 0.5, 0)
    local savedMainPos, savedM7Pos = nil, nil
    local mainVisible = true

    local bar = Instance.new("CanvasGroup")
    bar.Size = UDim2.new(0, 210, 0, 120)
    bar.Position = MAIN_DEFAULT
    bar.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
    bar.BackgroundTransparency = 0.15
    bar.BorderSizePixel = 0
    bar.Active = true
    bar.Parent = gui
    Instance.new("UICorner", bar).CornerRadius = UDim.new(0, 10)
    addStroke(bar, 0.6)

    local barLimit = Instance.new("UISizeConstraint")
    barLimit.MinSize = Vector2.new(180, 116)
    barLimit.MaxSize = Vector2.new(250, 126)
    barLimit.Parent = bar

    local barScale = Instance.new("UIScale")
    barScale.Parent = bar

    local dragHandle = Instance.new("Frame")
    dragHandle.Size = UDim2.new(1, 0, 1, 0)
    dragHandle.Position = UDim2.new(0, 0, 0, 0)
    dragHandle.BackgroundTransparency = 1
    dragHandle.Active = true
    dragHandle.ZIndex = 1
    dragHandle.Parent = bar

    local head = Instance.new("TextLabel")
    head.Size = UDim2.new(1, -84, 0, 18)
    head.Position = UDim2.new(0, 12, 0, 9)
    head.BackgroundTransparency = 1
    head.Text = "تفريم | M7"
    head.TextColor3 = Color3.fromRGB(225, 225, 232)
    head.Font = Enum.Font.Michroma
    head.TextScaled = true
    head.TextXAlignment = Enum.TextXAlignment.Left
    head.ZIndex = 2
    head.Parent = bar
    local headLimit = Instance.new("UITextSizeConstraint")
    headLimit.MaxTextSize = 12
    headLimit.MinTextSize = 7
    headLimit.Parent = head

    local closeBtn = Instance.new("TextButton")
    closeBtn.Size = UDim2.new(0, 24, 0, 24)
    closeBtn.Position = UDim2.new(1, -32, 0, 6)
    closeBtn.BackgroundColor3 = BTN_BG
    closeBtn.BackgroundTransparency = 0.65
    closeBtn.BorderSizePixel = 0
    closeBtn.Text = "X"
    closeBtn.TextColor3 = Color3.fromRGB(230, 230, 235)
    closeBtn.Font = Enum.Font.GothamBold
    closeBtn.TextSize = 13
    closeBtn.AutoButtonColor = false
    closeBtn.ZIndex = 5
    closeBtn.Parent = bar
    Instance.new("UICorner", closeBtn).CornerRadius = UDim.new(0, 6)
    addStroke(closeBtn, 0.6)

    local minBtn = Instance.new("TextButton")
    minBtn.Size = UDim2.new(0, 24, 0, 24)
    minBtn.Position = UDim2.new(1, -60, 0, 6)
    minBtn.BackgroundColor3 = BTN_BG
    minBtn.BackgroundTransparency = 0.65
    minBtn.BorderSizePixel = 0
    minBtn.Text = "-"
    minBtn.TextColor3 = Color3.fromRGB(230, 230, 235)
    minBtn.Font = Enum.Font.GothamBold
    minBtn.TextSize = 16
    minBtn.AutoButtonColor = false
    minBtn.ZIndex = 5
    minBtn.Parent = bar
    Instance.new("UICorner", minBtn).CornerRadius = UDim.new(0, 6)
    addStroke(minBtn, 0.6)

    local track = Instance.new("Frame")
    track.Size = UDim2.new(0, 46, 0, 26)
    track.Position = UDim2.new(0, 10, 0, 40)
    track.BackgroundColor3 = Color3.fromRGB(100, 100, 105)
    track.BorderSizePixel = 0
    track.ZIndex = 2
    track.Parent = bar
    Instance.new("UICorner", track).CornerRadius = UDim.new(1, 0)

    local knob = Instance.new("Frame")
    knob.Size = UDim2.new(0, 22, 0, 22)
    knob.Position = UDim2.new(1, -24, 0, 2)
    knob.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    knob.BorderSizePixel = 0
    knob.ZIndex = 3
    knob.Parent = track
    Instance.new("UICorner", knob).CornerRadius = UDim.new(1, 0)

    local toggleBtn = Instance.new("TextButton")
    toggleBtn.Size = UDim2.new(1, 0, 1, 0)
    toggleBtn.BackgroundTransparency = 1
    toggleBtn.AutoButtonColor = false
    toggleBtn.Text = ""
    toggleBtn.ZIndex = 4
    toggleBtn.Parent = track

    local title = Instance.new("TextLabel")
    title.Size = UDim2.new(1, -72, 0, 20)
    title.Position = UDim2.new(0, 62, 0, 38)
    title.BackgroundTransparency = 1
    title.Text = "بدأ التفريم"
    title.TextColor3 = Color3.fromRGB(210, 210, 215)
    title.Font = Enum.Font.GothamBold
    title.TextSize = 15
    title.TextXAlignment = Enum.TextXAlignment.Right
    title.TextYAlignment = Enum.TextYAlignment.Center
    title.ZIndex = 2
    title.Parent = bar

    local status = Instance.new("TextLabel")
    status.Size = UDim2.new(1, -72, 0, 13)
    status.Position = UDim2.new(0, 62, 0, 58)
    status.BackgroundTransparency = 1
    status.Text = "مطفي"
    status.TextColor3 = Color3.fromRGB(140, 140, 148)
    status.Font = Enum.Font.Gotham
    status.TextSize = 10
    status.TextXAlignment = Enum.TextXAlignment.Right
    status.TextYAlignment = Enum.TextYAlignment.Center
    status.TextTruncate = Enum.TextTruncate.AtEnd
    status.ZIndex = 2
    status.Parent = bar

    -- الصف الثاني: تغيير السيرفر تلقائيا و بدأ التفريم
    local sep = Instance.new("Frame")
    sep.Size = UDim2.new(1, -24, 0, 1)
    sep.Position = UDim2.new(0, 12, 0, 76)
    sep.BackgroundColor3 = GRAY
    sep.BackgroundTransparency = 0.7
    sep.BorderSizePixel = 0
    sep.ZIndex = 2
    sep.Parent = bar

    local track2 = Instance.new("Frame")
    track2.Size = UDim2.new(0, 46, 0, 26)
    track2.Position = UDim2.new(0, 10, 0, 84)
    track2.BackgroundColor3 = Color3.fromRGB(100, 100, 105)
    track2.BorderSizePixel = 0
    track2.ZIndex = 2
    track2.Parent = bar
    Instance.new("UICorner", track2).CornerRadius = UDim.new(1, 0)

    local knob2 = Instance.new("Frame")
    knob2.Size = UDim2.new(0, 22, 0, 22)
    knob2.Position = UDim2.new(1, -24, 0, 2)
    knob2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    knob2.BorderSizePixel = 0
    knob2.ZIndex = 3
    knob2.Parent = track2
    Instance.new("UICorner", knob2).CornerRadius = UDim.new(1, 0)

    local toggleBtn2 = Instance.new("TextButton")
    toggleBtn2.Size = UDim2.new(1, 0, 1, 0)
    toggleBtn2.BackgroundTransparency = 1
    toggleBtn2.AutoButtonColor = false
    toggleBtn2.Text = ""
    toggleBtn2.ZIndex = 4
    toggleBtn2.Parent = track2

    local title2 = Instance.new("TextLabel")
    title2.Size = UDim2.new(1, -72, 0, 28)
    title2.Position = UDim2.new(0, 62, 0, 80)
    title2.BackgroundTransparency = 1
    title2.Text = "تغيير السيرفر تلقائيا و بدأ التفريم"
    title2.TextColor3 = Color3.fromRGB(210, 210, 215)
    title2.Font = Enum.Font.GothamBold
    title2.TextSize = 11
    title2.TextWrapped = true
    title2.TextXAlignment = Enum.TextXAlignment.Right
    title2.TextYAlignment = Enum.TextYAlignment.Center
    title2.ZIndex = 2
    title2.Parent = bar

    local status2 = Instance.new("TextLabel")
    status2.Size = UDim2.new(1, -72, 0, 13)
    status2.Position = UDim2.new(0, 62, 0, 104)
    status2.BackgroundTransparency = 1
    status2.Text = "مطفي"
    status2.TextColor3 = Color3.fromRGB(140, 140, 148)
    status2.Font = Enum.Font.Gotham
    status2.TextSize = 10
    status2.TextXAlignment = Enum.TextXAlignment.Right
    status2.TextYAlignment = Enum.TextYAlignment.Center
    status2.TextTruncate = Enum.TextTruncate.AtEnd
    status2.ZIndex = 2
    status2.Parent = bar

    local m7Btn = Instance.new("TextButton")
    m7Btn.Size = UDim2.new(0, 46, 0, 46)
    m7Btn.AnchorPoint = Vector2.new(0.5, 0.5)
    m7Btn.Position = M7_DEFAULT
    m7Btn.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
    m7Btn.BackgroundTransparency = 0.15
    m7Btn.BorderSizePixel = 0
    m7Btn.Text = "M7"
    m7Btn.TextColor3 = Color3.fromRGB(235, 235, 240)
    m7Btn.Font = Enum.Font.Michroma
    m7Btn.TextSize = 14
    m7Btn.AutoButtonColor = false
    m7Btn.Visible = false
    m7Btn.ZIndex = 5
    m7Btn.Parent = gui
    Instance.new("UICorner", m7Btn).CornerRadius = UDim.new(0, 12)
    local m7Stroke = addStroke(m7Btn, 0.6)

    local overlay = Instance.new("CanvasGroup")
    overlay.Size = UDim2.new(1, 0, 1, 0)
    overlay.BackgroundTransparency = 1
    overlay.BorderSizePixel = 0
    overlay.Visible = false
    overlay.ZIndex = 10
    overlay.Parent = gui

    local dialog = Instance.new("Frame")
    dialog.Size = UDim2.new(0, 220, 0, 120)
    dialog.AnchorPoint = Vector2.new(0.5, 0.5)
    dialog.Position = UDim2.new(0.5, 0, 0.5, 0)
    dialog.BackgroundColor3 = Color3.fromRGB(20, 20, 24)
    dialog.BorderSizePixel = 0
    dialog.ZIndex = 11
    dialog.Parent = overlay
    Instance.new("UICorner", dialog).CornerRadius = UDim.new(0, 10)
    addStroke(dialog, 1)

    local dlgLimit = Instance.new("UISizeConstraint")
    dlgLimit.MinSize = Vector2.new(200, 110)
    dlgLimit.MaxSize = Vector2.new(260, 130)
    dlgLimit.Parent = dialog

    local dlgScale = Instance.new("UIScale")
    dlgScale.Parent = dialog

    local dlgText = Instance.new("TextLabel")
    dlgText.Size = UDim2.new(1, -20, 0, 50)
    dlgText.Position = UDim2.new(0, 10, 0, 12)
    dlgText.BackgroundTransparency = 1
    dlgText.Text = "هل أنت متأكد من حذف القائمة؟"
    dlgText.TextColor3 = Color3.fromRGB(220, 220, 225)
    dlgText.Font = Enum.Font.GothamBold
    dlgText.TextSize = 14
    dlgText.TextWrapped = true
    dlgText.TextXAlignment = Enum.TextXAlignment.Center
    dlgText.ZIndex = 12
    dlgText.Parent = dialog

    local function dlgButton(text, pos)
        local b = Instance.new("TextButton")
        b.Size = UDim2.new(0, 85, 0, 34)
        b.Position = pos
        b.BackgroundColor3 = BTN_BG
        b.BackgroundTransparency = 0.1
        b.BorderSizePixel = 0
        b.AutoButtonColor = false
        b.Text = text
        b.TextColor3 = Color3.fromRGB(230, 230, 235)
        b.Font = Enum.Font.GothamBold
        b.TextSize = 14
        b.ZIndex = 12
        b.Parent = dialog
        Instance.new("UICorner", b).CornerRadius = UDim.new(0, 6)
        addStroke(b, 0.6)
        return b
    end
    local yesBtn = dlgButton("نعم", UDim2.new(0, 15, 1, -46))
    local noBtn  = dlgButton("لا", UDim2.new(1, -100, 1, -46))

    pressFX(closeBtn)
    pressFX(minBtn)
    pressFX(yesBtn)
    pressFX(noBtn)
    pressFX(toggleBtn, track)
    pressFX(toggleBtn2, track2)

    local dotBase  = nil
    local dotCount = 3
    local lastRaw  = nil
    local curText  = "مطفي"

    -- النص الحي يطلع تحت الزر الشغال، والثاني "مطفي"
    local function render()
        if HOP.on and running then
            status.Text, status2.Text = "مطفي", curText
        else
            status.Text, status2.Text = curText, "مطفي"
        end
    end

    setStatus = function(text, force)
        if (not force) and (not running) then return end
        if not status.Parent then return end
        if text == lastRaw then return end
        lastRaw = text

        local base = string.match(text, "^(.-)%.%.%.$")
        if base then
            dotBase  = base
            dotCount = 1
            curText = base .. "."
            render()
        else
            dotBase = nil
            curText = text
            render()
        end
    end

    task.spawn(function()
        while status.Parent do
            task.wait(CFG.DOTS_INTERVAL)
            if dotBase and status.Parent then
                dotCount = dotCount % 3 + 1
                curText = dotBase .. string.rep(".", dotCount)
                render()
            end
        end
    end)

    local function paint(trk, kn, on)
        if not trk.Parent then return end
        TweenService:Create(trk, TweenInfo.new(0.25, Enum.EasingStyle.Quad), {
            BackgroundColor3 = on and Color3.fromRGB(0, 122, 255) or Color3.fromRGB(100, 100, 105)
        }):Play()
        TweenService:Create(kn, TweenInfo.new(0.25, Enum.EasingStyle.Quad), {
            Position = on and UDim2.new(0, 2, 0, 2) or UDim2.new(1, -24, 0, 2)
        }):Play()
    end

    -- يحدّث شكل الزرين حسب الحالة الحالية (running / HOP.on)
    setVisual = function()
        paint(track, knob, running and not HOP.on)
        paint(track2, knob2, running and HOP.on)
        render()
    end

    local HALF_W, HALF_H = 105, 60
    local animDriver = Instance.new("NumberValue")
    local animBase = MAIN_DEFAULT
    local animTween = nil
    local animRunning = false

    local function restPos()
        return savedMainPos or MAIN_DEFAULT
    end

    local function applyMain(v)
        local s = 0.86 + 0.14 * v
        barScale.Scale = s
        bar.GroupTransparency = math.clamp(1 - v, 0, 1)
        bar.Position = UDim2.new(
            animBase.X.Scale, animBase.X.Offset + (1 - s) * HALF_W,
            animBase.Y.Scale, animBase.Y.Offset + (1 - s) * HALF_H + (1 - v) * 10)
    end
    animDriver.Changed:Connect(applyMain)

    local function playMain(target, dur, style, dirE)
        if animTween then animTween:Cancel(); animTween = nil end
        if not animRunning then animBase = restPos() end
        animRunning = true
        if target == 1 then bar.Visible = true end
        local tw = TweenService:Create(animDriver, TweenInfo.new(dur, style, dirE), {Value = target})
        animTween = tw
        tw.Completed:Connect(function()
            if animTween ~= tw then return end
            animTween = nil
            animRunning = false
            bar.Position = restPos()
            if target == 0 then bar.Visible = false end
        end)
        tw:Play()
    end

    local function showMain()
        mainVisible = true
        playMain(1, 0.5, Enum.EasingStyle.Back, Enum.EasingDirection.Out)
    end

    local function hideMain()
        mainVisible = false
        playMain(0, 0.28, Enum.EasingStyle.Quad, Enum.EasingDirection.In)
    end

    local m7Scale = Instance.new("UIScale")
    m7Scale.Parent = m7Btn
    local m7Pop, m7Fx = 0, 1
    local m7PopDrv = Instance.new("NumberValue")
    m7PopDrv.Value = 0
    local m7FxDrv = Instance.new("NumberValue")
    m7FxDrv.Value = 1

    local function applyM7()
        local t = math.clamp(1 - m7Pop, 0, 1)
        m7Scale.Scale = math.max(m7Pop, 0.01) * m7Fx
        m7Btn.BackgroundTransparency = 0.15 + 0.85 * t
        m7Btn.TextTransparency = t
        m7Stroke.Transparency = 0.45 + 0.55 * t
    end
    applyM7()
    m7PopDrv.Changed:Connect(function(v) m7Pop = v; applyM7() end)
    m7FxDrv.Changed:Connect(function(v) m7Fx = v; applyM7() end)

    local m7Tween = nil
    local function setM7(show)
        if m7Tween then m7Tween:Cancel() end
        if show then m7Btn.Visible = true end
        local tw = TweenService:Create(m7PopDrv,
            TweenInfo.new(show and 0.45 or 0.22, show and Enum.EasingStyle.Back or Enum.EasingStyle.Quad,
                show and Enum.EasingDirection.Out or Enum.EasingDirection.In),
            {Value = show and 1 or 0})
        m7Tween = tw
        tw.Completed:Connect(function()
            if m7Tween == tw and not show then m7Btn.Visible = false end
        end)
        tw:Play()
    end

    m7Btn.InputBegan:Connect(function(i)
        if isPointer(i) then
            TweenService:Create(m7FxDrv, TweenInfo.new(0.12, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Value = 0.92}):Play()
            TweenService:Create(m7Stroke, TweenInfo.new(0.12), {Thickness = 1.5}):Play()
        end
    end)
    m7Btn.InputEnded:Connect(function(i)
        if isPointer(i) then
            TweenService:Create(m7FxDrv, TweenInfo.new(0.2, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {Value = 1}):Play()
            TweenService:Create(m7Stroke, TweenInfo.new(0.15), {Thickness = 0.6}):Play()
        end
    end)
    if UIS.MouseEnabled then
        m7Btn.MouseEnter:Connect(function()
            TweenService:Create(m7FxDrv, TweenInfo.new(0.12), {Value = 1.08}):Play()
        end)
        m7Btn.MouseLeave:Connect(function()
            TweenService:Create(m7FxDrv, TweenInfo.new(0.15), {Value = 1}):Play()
            TweenService:Create(m7Stroke, TweenInfo.new(0.15), {Thickness = 0.6}):Play()
        end)
    end

    local dlgOpen, dlgToken = false, 0
    local function showDialog()
        if dlgOpen then return end
        dlgOpen = true
        dlgToken = dlgToken + 1
        overlay.GroupTransparency = 1
        dlgScale.Scale = 0.8
        overlay.Visible = true
        TweenService:Create(overlay, TweenInfo.new(0.2, Enum.EasingStyle.Quad), {GroupTransparency = 0}):Play()
        TweenService:Create(dlgScale, TweenInfo.new(0.35, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {Scale = 1}):Play()
    end
    local function hideDialog()
        if not dlgOpen then return end
        dlgOpen = false
        dlgToken = dlgToken + 1
        local my = dlgToken
        TweenService:Create(overlay, TweenInfo.new(0.18, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {GroupTransparency = 1}):Play()
        TweenService:Create(dlgScale, TweenInfo.new(0.18, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {Scale = 0.9}):Play()
        task.delay(0.2, function()
            if my == dlgToken and overlay.Parent then overlay.Visible = false end
        end)
    end

    local function fullCleanup()
        pcall(stopAll)
        pcall(resetState)
        ENV.M7_AllCleanup = nil
        pcall(function() gui:Destroy() end)
        if Stunts.keyGui then pcall(function() Stunts.keyGui:Destroy() end) end
        myGui = nil
    end
    ENV.M7_AllCleanup = fullCleanup

    setupSmoothDrag(dragHandle, bar, function(pos) savedMainPos = pos end)
    local m7Drag = setupSmoothDrag(m7Btn, m7Btn, function(pos) savedM7Pos = pos end)
    if savedM7Pos then m7Btn.Position = savedM7Pos end

    -- حفظ حالة الأزرار (تنرجع تلقائي بعد تغيير السيرفر من السكربت)
    local function persist()
        HOP.set.farm = running
        HOP.set.hop = running and HOP.on
        HOP.save()
    end

    local function beginFarm(hop)
        HOP.on = hop
        HOP.lastTry = -100
        startAll()
        setStatus("يبدأ...", true)
        setVisual()
        persist()
    end

    -- زر بدأ التفريم (بدون تغيير سيرفر)
    toggleBtn.Activated:Connect(function()
        playClick()
        if running and HOP.on then
            HOP.on = false           -- يكمل تفريم عادي بدون تغيير سيرفر
            HOP.crowded = false
            setVisual()
            persist()
        elseif running then
            stopAll()
            persist()
        else
            beginFarm(false)
        end
    end)

    -- زر تغيير السيرفر تلقائيا و بدأ التفريم
    toggleBtn2.Activated:Connect(function()
        playClick()
        if running and HOP.on then
            stopAll()
            persist()
        elseif running then
            HOP.on = true            -- يفعّل تغيير السيرفر على التفريم الشغال
            HOP.lastTry = -100
            setVisual()
            persist()
        else
            beginFarm(true)
        end
    end)

    minBtn.Activated:Connect(function()
        playClick()
        hideDialog()
        hideMain()
        setM7(true)
    end)

    m7Btn.MouseButton1Click:Connect(function()
        if m7Drag.wasMoved() then return end
        playClick()
        showMain()
        setM7(false)
    end)

    closeBtn.Activated:Connect(function()
        playClick()
        showDialog()
    end)

    noBtn.Activated:Connect(function()
        playClick()
        hideDialog()
    end)

    local deleting = false
    yesBtn.Activated:Connect(function()
        if deleting then return end
        deleting = true
        playClick()
        hideDialog()
        HOP.set.farm, HOP.set.hop = false, false
        HOP.set.hopJob = nil
        HOP.save()
        pcall(stopAll)
        pcall(resetState)
        ENV.M7_AllCleanup = nil
        playMain(0, 0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.In)
        if m7Btn.Visible then setM7(false) end
        task.delay(0.6, function()
            pcall(function() gui:Destroy() end)
            myGui = nil
            Stunts.notify("تم حذف القائمة", 5)
            task.delay(5.8, function()
                if Stunts.keyGui then pcall(function() Stunts.keyGui:Destroy() end) end
            end)
        end)
    end)

    animBase = restPos()
    applyMain(0)
    task.defer(function()
        playMain(1, 0.65, Enum.EasingStyle.Back, Enum.EasingDirection.Out)
    end)

    -- تشغيل تلقائي فقط لو دخل بتغيير السيرفر من السكربت (مو دخول يدوي)
    if HOP.arrived and HOP.set.farm then
        task.spawn(function()
            local t0 = os.clock()
            repeat task.wait(0.2) until (getHRP() and getHum()) or os.clock() - t0 > 25
            task.wait(CFG.AUTOSTART_DELAY)
            if running then return end
            HOP.on = HOP.set.hop
            HOP.lastTry = -100
            -- لو السيرفر مزدحم (أكثر من المتوقع) يغيّر علطول بدون تفريم
            if HOP.on then
                local count = #Players:GetPlayers()
                local limit = math.max(CFG.HOP_MAX_PLAYERS, (HOP.expect or 0) + 4)
                if count > limit then
                    HOP.crowded = true
                    dbg("دخل سيرفر مزدحم:", count, "لاعبين (الحد", limit, ")")
                end
            end
            startAll()
            setStatus("يبدأ...", true)
            setVisual()
        end)
    end
end

print("M7 v39 | غسيل موحّد | إصلاح الغسيل بعد تغيير السيرفر | تغيير سيرفر لأفضى سيرفر | بدون شراء بعد الغسيل بوضع تغيير السيرفر | تجميد الحركة | قفل حزمة الشراء | نظام المفاتيح | Anti-AFK")
