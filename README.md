local teleportEnabled = false

local function teleportToDummy()
    local dummy2 = workspace.MAP:FindFirstChild("5k_dummies")
    if dummy2 and dummy2:FindFirstChild("Dummy2") then
        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(dummy2.Dummy2.HumanoidRootPart.CFrame)
        print("Téléportation réussie.")
    else
        print("Le Dummy2 n'existe pas.")
    end
end

local function toggleTeleport()
    teleportEnabled = not teleportEnabled
    if teleportEnabled then
        print("Téléportation activée.")
    else
        print("Téléportation désactivée.")
    end
end

local function sendToServer()
    while true do
        wait()
        if teleportEnabled then
            local dummy2 = workspace.MAP:FindFirstChild("5k_dummies")
            if dummy2 and dummy2:FindFirstChild("Dummy2") then
                local args = {
                    [1] = dummy2.Dummy2.Humanoid,
                    [2] = 1
                }
                game:GetService("ReplicatedStorage").jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(unpack(args))
                print("Données envoyées au serveur.")
            else
                print("Le Dummy2 n'existe pas.")
            end
        end
    end
end

toggleTeleport()
coroutine.wrap(sendToServer)()
