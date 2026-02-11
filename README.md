```lua
local UILibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/zxcursedsocute/UI-Library/refs/heads/main/UI-Library.txt"))()

local windows = UILibrary.CreateWindow("CursedSaken v1.3.1 ","","590","480")

local Settings = windows:AddTab("UI settings","Settings")

Settings:AddSection('Interface')

Settings:AddDropdown({
	Name = 'Theme',
	Description = 'Change the interface theme',
	Options = {'Darkness','Dark','White','Black','Forsaken',"Forest 2021",'Germany 1941','Spooky'},
	Default = 'Darkness',
	Callback = function(select)
		windows:SetTheme(select)
	end
})

SetBlur = Settings:AddToggle({
	Name = 'Blur',
	Description = 'Need graphics level of 8 and above',
	Callback = function(state)
		if state  then
			windows:Blur()
		else
                        windows:BlurOff()
		end
	end
})

SetTransparancy = Settings:AddToggle({
	Name = 'Transparancy',
	Description = 'Change The Background Transparancy',
	Callback = function(state)
		windows:ChangeBackgroundTransparance()
	end
})

SetUserInfo = Settings:AddToggle({
	Name = 'User info',
	Description = 'Show info about your account',
	Callback = function(state)
		windows:UserInfo()
	end
})

Settings:AddToggle({
	Name = 'Search',
	Description = 'Show the search',
	Callback = function(state)
		windows:ShowSearch()
	end
})

Settings:AddSection('Window')

Settings:AddKeybind({
	Name = "Minimaze Window",
	Description = "Change the window to minimaze",
	Default = '',
	Callback = function()
		windows:Minimaze()
	end
})

Settings:AddKeybind({
	Name = "Column Window",
	Description = "Change the window to column",
	Default = '',
	Callback = function()
		windows:ColumnWindow()
	end
})

Settings:AddKeybind({
	Name = "Close Window",
	Description = "Close the Window",
	Default = Enum.KeyCode.LeftAlt,
	Callback = function()
		windows:Close()
	end
})

Settings:AddSection('Config')

Settings:AddToggle({
	Name = 'Load Config',
	Description = 'loads the saved script settings',
	Callback = function(state)
	if state then
		windows:LoadConfig("zxcursedsocute/forsaken.json")
	end
	end,
})

local SaveConfigCon = nil
Settings:AddToggle({
	Name = 'Save Config',
	Description = 'Saves the current script settings',
	Callback = function(state)
		if SaveConfigCon then 
            SaveConfigCon:Disconnect()
            SaveConfigCon = nil
		end
	    if state then
            windows:SaveConfig("zxcursedsocute","forsaken.json")
            SaveConfigCon = game.Players.PlayerRemoving:Connect(function(plr)
                if plr.DisplayName == game.Players.LocalPlayer.DisplayName then
                    windows:SaveConfig("zxcursedsocute","forsaken.json")
                end
	        end)
		end
	end
})

Settings:AddButton({
	Name = 'Get Config',
	Description = 'copies the current config to the clipboard',
	Callback = function()
		windows:GetConfig("zxcursedsocute/forsaken.json")
	end,
})

Settings:AddInput({
	Name = 'Input Config',
	Description = '',
	SaveConfig = true,
	Callback = function(text)
		windows:InputConfig("zxcursedsocute/forsaken.json",text)
	end,
})

Settings:AddSection('Version (1.3.1)')

Settings:AddParagraph("version 1.0", "Created at 07.08.25 (v 1.0)", "Updated at 11.09.25 (v 1.3.1)")

windows:Notification({
	Name = 'Notfication',
	Description = 'The library has been loaded.',
	Type = 'Notification',
	Duration = 10
})

windows:IsLoadConfig("zxcursedsocute/forsaken.json")

windows:ScaleForMobileFixed()
```
