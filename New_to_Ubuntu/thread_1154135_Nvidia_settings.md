---
title: "Nvidia settings"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by brander on 2009-05-09
Looks like I`m one of the lucky ones with 9.04, my NVidia card works perfectly and it selects the correct res for my monitor. But it chooses 75 Hz refresh rate and I want 60.

I can change it in the nvidia settings and it is then fine but it is unable to save the settings for next time. When I press the save to x configuration file, it gives the path and filename but when I press "save", I get this:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'

It looks to me like a linux permissions problem to me rather than a nvidia one, can anyone help on this?

---

### Post by ibuclaw on 2009-05-09
Press **Alt+F2** and type in:
```
gksu nvidia-settings
```

Regards
Iain

---

### Post by fooman on 2009-05-09
you will need to run nvidia settings with root privileges in order to make them "stick".

open a terminal and type or copy/paste the following:

```
gksudo nvidia-settings
```make the changes, save to x-config and you should be set.

hope that helps.

edit: i am too slow...again!

---

### Post by brander on 2009-05-09
Thanks, that worked so it will probably be right next startup.

---

### Post by Ms_Angel_D on 2009-05-09
Just as aside, I use Nvidia myself, and the first thing I do after it installs the settings manager is edit the menu entry and add gksu to the front of the command, that way it will open as root, and the settings will always stick.

---

### Post by drjonze on 2009-05-09
> **MetalHellsAngel said:**
> Just as aside, I use Nvidia myself, and the first thing I do after it installs the settings manager is edit the menu entry and add gksu to the front of the command, that way it will open as root, and the settings will always stick.

That is such a simple trick that I never would have thought of. Thanks!

---

