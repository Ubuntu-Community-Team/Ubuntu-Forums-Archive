---
title: "Visual effects"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by vishwasmeshram on 2010-11-15
Hi,
Last night after getting some update i lost my Visual effects.When i tried to regain it it shows "Desktop effects could not be enabled".:(
Thanx in advanced!!!

---

### Post by stoogiebuncho on 2010-11-15
Have you restarted your computer?  I know that's usually a Windows solution, but occasionally it can fix problems in Ubuntu as well.

---

### Post by vishwasmeshram on 2010-11-15
yes i restart my lappy for several time but cant fix it.
when i try to select extra visual effect it searches for drivers and again show me same msg...

---

### Post by freesitebuilder on 2010-11-15
What video card does it have?

---

### Post by vishwasmeshram on 2010-11-16
ATI Radeon X2300 256 mb

---

### Post by mastablasta on 2010-11-16
Did you do update or upgrade? because if you upgraded you would have to first remove the drivers, then do upgrade then (re)install new drivers.

---

### Post by toekneewood on 2010-11-16
If you are using compiz then you do not need to touch your desktop settings when you right click your desktop and change the visual affects settings.  If you are not using compiz then give it a go
```

sudo apt-get install compizconfig-settings-manager

```
Then go to the menu and select "system, preferences, CompizConfig Settings Manager"

You will find LOOOOOOOOAAAAAD's of settings, including the cube affect.

---

### Post by vishwasmeshram on 2010-11-16
I have not upgrade my lappy .As you suggest i download compiz but yet not able to get effect .
Can u tell me how to remove driver .

---

### Post by sky_ceiling on 2010-11-16
in the terminal type compiz --replace

what does it say?

---

### Post by vishwasmeshram on 2010-11-16
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_1"
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1800003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1800003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

---

### Post by vishwasmeshram on 2010-11-20
is there anybody who can help???????

---

