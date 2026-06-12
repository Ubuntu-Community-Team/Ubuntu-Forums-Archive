---
title: "video card drivers revert after reboot"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by jager8113 on 2009-01-15
I have a nvidia 8600gt video card...I can install the latest drivers, but when i reboot it reverts to low graphics mode...I have to reinstall the drivers each time I restart...Is there a config file I am supposed to edit? Thank you for your help!!

---

### Post by beastrace91 on 2009-01-15
How are you installing the drivers? Also you might wanna check to see what driver is being used in your xorg.conf, I don't remember the path to this file off the top of my head, and see which one is in use when you are getting "low resolution" mode.

~Jeff

---

### Post by jager8113 on 2009-01-15
I got the drivers via nvidias website...i hit ctrl+alt+f1..then type
/etc/initd.d/gdm stop
then i install the drivers and restart the above file...THis brings me to the logon screen with my drives correctly running..

---

### Post by beastrace91 on 2009-01-16
Check at see what is listed under the "Driver" in your xorg.conf both when your drivers are working and when they are not (maybe they are different/not getting edited properly) to see this run ```
sudo nano /etc/X11/xorg.conf
```

Also wanna provide some more detail on your system/setup?

~Jeff

---

