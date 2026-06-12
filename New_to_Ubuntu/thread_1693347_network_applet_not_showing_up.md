---
title: "network applet not showing up"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by jhchughes on 2011-02-22
I'm running Ubuntu 10.10 on a chrome notebook, and after a few days of use, it stopped showing the Network/wireless indicator/applet on the main top panel. This is incredibly annoying cause I can't connect to the internet (I'm posting from a different comp.) 

Any help would be greatly appreciated. 
-j

---

### Post by G4Oblivion on 2011-02-22
Try ```
killall gnome-panel
```.
If that doesn't work, the only other way **I** know is to reset gnome.

It may be part of one of the applets under "Add to panel"

---

### Post by jhchughes on 2011-02-22
I tried that, but it says "gnome-panel(1104): operation not permitted."

---

### Post by G4Oblivion on 2011-02-22
> **jhchughes said:**
> I tried that, but it says "gnome-panel(1104): operation not permitted."

I'm guessing 1104 means natty? (Ubuntu 11.04) or is it an error message.
I've never used natty, so it may not work.

Did you try ```
sudo killall gnome-panel
```?

EDIT:

Try right clicking the panel and click "Add to panel"
Select "Notification area"

---

### Post by jhchughes on 2011-02-22
Yeah. I just tried it with sudo, and that killed it. But a second later it came back, still without a network applet.

---

### Post by grahammechanical on 2011-02-22
Right click the top panel, select Add to Panel. Tick Notification Area. Also make sure that Network Manager is ticked as one of the Startup Applications in System>Preferences>Startup Applications. May be re-boot.

Regards,

---

