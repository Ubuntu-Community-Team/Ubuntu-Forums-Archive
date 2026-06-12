---
title: "Ubuntu Graphics Modes Not Working"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by nu2buntu0 on 2010-06-05
Alright so, yes even though I have used normal graphics mode on my Ubuntu in the past it seems as if it stopped working and now I can only work with no desktop effects (Kinda ruins the fun :/)

Anyway, it seems as if it works sometimes when I reinstall my appropriate driver and restart.

How can I get my Nvidia to normal graphics mode? 

Thank you

---

### Post by cariboo on 2010-06-05
You may need to create a new /etc/X11/xorg.conf, open a terminal and type:

```
sudo nvidia-xconfig
```

Once the new file has been created, reboot, and you should be taken back to a working desktop.

---

