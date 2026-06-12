---
title: "So I decided to uninstall everything compiz..."
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Mrent on 2009-02-12
And now all my windows are static. Is there a list of default compiz packages that are used by ubuntu ? I just want to get ubuntu to the way it was before (without installing all the compiz packages). Also I am using Ubuntu 8.10.

---

### Post by x33a on 2009-02-12
what do you mean by windows are static?

---

### Post by mcduck on 2009-02-12
if you mean that your windows are missing borders and you can't move them around you simply need to start some other window manager than Compiz.

Run "metacity --replace" to enable Gnome's own window manager. Or disable the desktop effects in the System/Preferences-menu, disabling them will switch you to Metacity as well..

---

### Post by geirha on 2009-02-12
Installing the package [ubuntu-desktop](apt:ubuntu-desktop) should get your desktop back to normal.

---

### Post by minsf on 2009-02-12
what kind of video card do you have? what driver are you using? please post here the output of ```
sudo lshw -C display
```

> **mcduck said:**
> if you mean that your windows are missing borders and you can't move them around you simply need to start some other window manager than Compiz.

to draw windows' borders (at least with nvidia), try to add the following line to the Screen section in your xorg.conf ```
Option  "AddARGBGLXVisuals"  "True"
```(and then, of course, restart X)
to move a window without a border, use alt+F7.
but then, we dont know that this is what the original poster means by "static".

like mcduck said, to go back to "normal", enter in from the command line:```
metacity --replace
```

it may be interesting to know how oyu installed compiz. to this end, please post here the output of ```
sudo dpkg -l| grep compiz
```

you may want to install the package compizconfig-settings-manager to control compiz's settings (after installation go to System>Preferences>Compiz to change the settings). for more about compiz, you may be interested in the following link:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by Mrent on 2009-02-12
Thanks for the replies. I managed to get everything back to normal through 

-$ sudo apt-get install ubuntu-desktop

To clarify my problem albeit a a little late, after I removed every package associated with compiz, I found I could not move around my windows, and the close and minimize buttons where missing as well. After installing ubuntu-desktop everything went back to normal!

Thank you everyone once again.

---

