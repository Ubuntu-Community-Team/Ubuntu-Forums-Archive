---
title: "wine problems"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2009-06-17
I just installed wine on my 64-bit Jaunty computer and there is not a wine folder under the applications menu like there is supposed to be. When i go to System -> Preferences -> Main Menu, it does not show up there either. Instead it says that a single application called Wine Windows Program Loader is under Other. This is not right either because when I run that nothing happens. I have wine installed on my other computer and it works fine. Any ideas?

---

### Post by achase79 on 2009-06-17
what version of wine do you have? From ubuntu or from winehq.org?

---

### Post by Indian_Guy101 on 2009-06-17
well I can't really tell what version of wine i have. I just installed playonlinux so i guess i am fine now.

---

### Post by Peterfc on 2009-06-18
Hi

If WINE is in the same place as mine. Go to Places/ home folder /View and go to Show hidden files. If you tick this box you will get all files that are hidden listed. On my machine this shows all the programs i use.

Hope that helps

---

### Post by Indian_Guy101 on 2009-06-19
Yes I know that. However, I am trying to get the Wine folder to show under the Applications menu at the top. Usually there is a wine icon there which has the options browse virtual C Drive, uninstall wine programs, and view installed programs. However, there is no icon under the applications menu.

---

### Post by 4Orbs on 2009-06-19
You might try checking the menu configuration by right-click on the "Applications" button and select Edit Menus, then navigate to the "Other" section and see if the additional options for Wine are un-checked which would prevent them from showing on the menu.

---

### Post by Indian_Guy101 on 2009-06-19
THere is only one option for Wine under that menu and that is already checked, Wine Windows Program Loader. It does not have the icon of the wine glass and when I navigate to it and click on it from the applications menu, nothing happens.

---

### Post by 4Orbs on 2009-06-19
When you installed wine, did you do the initial configuration by opening the (from a terminal) winecfg and selecting the audio driver and auto-detect of the drives? This first-run config rebuilds the Applications menu and also creates the .wine hidden folder in your personal home directory. You might need to log-out after the initial configuration for the menus to show up.

---

### Post by Indian_Guy101 on 2009-06-19
no initial configuration showed up. Maybe I installed it wrong. COuld you please give me instructions for installing wine from the terminal. All i did was sudo apt-get install wine. Nothing else.

---

### Post by 4Orbs on 2009-06-19
It sounds like you already have it installed, so to configure wine:
1. Open the Wine Configuration tool by entering this in a terminal...
```
winecfg
```
2. Click on the Audio tab of the Wine Configuration tool. It will take a few moments to open while it detects your audio drivers. Once open it will probably have already selected Alsa driver. You can click the "test" button and make sure you hear the test sound. If you are on an older computer, you might need to select the OSS sound driver to get sound from some games but you won't know until the situation arises. After selecting the audio driver of your choice click the apply button.
3. Click on the "Drives" tab of the Wine Config tool, then click the "Autodetect" button and you will see the list of detected drives appear.
4. Click "Apply", save and close the Wine Configuration tool.
5. Log out and back in, or better yet reboot.
6. The Applications menu should now have the other Wine stuff showing.
7. Now you can start installing Windows applications with Wine. Just double click on the "app-name.exe" file and Wine should automatically engage the installer. But first you should right-click on the .exe file and select Properties, then select "Open With" Wine loader.

---

### Post by Indian_Guy101 on 2009-06-19
I did exactly what you said, still no luck :cry:

---

### Post by 4Orbs on 2009-06-19
Then I am assuming you were able to open the Wine Configuration tool. Have you tried installing any Windows programs yet? I would suggest something small at first, maybe Photo Filtre or Color Picker. Both of those work well on my wine.

---

### Post by Indian_Guy101 on 2009-06-19
I was able to run PortableApps from my flash drive using wine, but I have not actually installed any windows programs yet. But how would that help in any way?

---

### Post by 4Orbs on 2009-06-19
Because whenever you install a new app it should force wine to build a new menu.

---

