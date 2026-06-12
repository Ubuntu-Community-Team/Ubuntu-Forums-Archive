---
title: "Different wallpapers for desktops"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Caramin on 2010-02-08
I'd like to have different Wallpapers for my desktops. Im using 9.10. After googeling i found..   Re: Can I Make Each Workspace Have a Different Wallpaper To have different wallpapers for each desktop, follow these steps:  I. Disable &quot;show desktop&quot; in Nautilus 1. ALT+F2 2. gconf-editor 3. Apps --> Nautilus --> Preferences 4. Untick &quot;show desktop&quot;  II. Install Compiz Fusion 1. In Terminal, input the following: Code:  sudo aptitude install compizconfig-settings-manager  2. Exit Terminal  III. Select your desktop wallpaper 1. System --> Preferences --> Advanced Desktop Settings 2. Tick &quot;Desktop Cube&quot; and opt to disable desktop wall if prompted 3. Tick &quot;Rotate Cube&quot; 4. Select &quot;Desktop Cube&quot; 5. Click &quot;Appearance&quot; tab 6. Click &quot;Add&quot; under the &quot;Background Images&quot; field 7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear    ... in this forum. Everything worked until I exited the Terminal. Can anyone help, please? Was that another version?  or something? THX __________________

---

### Post by tom.swartz07 on 2010-02-08
> **Caramin said:**
> I'd like to have different Wallpapers for my desktops. Im using 9.10. After googeling i found..   Re: Can I Make Each Workspace Have a Different Wallpaper To have different wallpapers for each desktop, follow these steps:  I. Disable &quot;show desktop&quot; in Nautilus 1. ALT+F2 2. gconf-editor 3. Apps --> Nautilus --> Preferences 4. Untick &quot;show desktop&quot;  II. Install Compiz Fusion 1. In Terminal, input the following: Code:  sudo aptitude install compizconfig-settings-manager  2. Exit Terminal  III. Select your desktop wallpaper 1. System --> Preferences --> Advanced Desktop Settings 2. Tick &quot;Desktop Cube&quot; and opt to disable desktop wall if prompted 3. Tick &quot;Rotate Cube&quot; 4. Select &quot;Desktop Cube&quot; 5. Click &quot;Appearance&quot; tab 6. Click &quot;Add&quot; under the &quot;Background Images&quot; field 7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear    ... in this forum. Everything worked until I exited the Terminal. Can anyone help, please? Was that another version?  or something? THX __________________

I dont mean to sound difficult, but could you perhaps clean up the post? It is really difficult to read.


That being said, from what I could understand from the post:
You should open compiz-config from system>preferences and then follow the rest of the instructions.

---

### Post by Caramin on 2010-02-08
Sorry, somehow it made everything appear as one text.  I'd like to have different Wallpapers for my desktops. Im using 9.10. After googeling i found..   [http://ubuntuforums.org/showthread.php?t=17359](http://ubuntuforums.org/showthread.php?t=17359)   in this forum. Everything worked until I exited the Terminal. Can anyone help, please? Was that another version? or something?   OK I found the place you told me and followed the instructions, but unfortunately - even with 3 Pics none appears on the second desctop...

---

### Post by Caramin on 2010-02-08
...and everything appears in one text again - is there any trick - cause when writing I do make  empty lines.. :)

---

### Post by ubername on 2010-02-08
Try putting the images in the 'wallpaper' setting in compizconfigsettings manager (under 'utilities') rather than in the 'desktop cube' settings

---

### Post by Caramin on 2010-02-08
That worked!  Thank you both!!!

---

