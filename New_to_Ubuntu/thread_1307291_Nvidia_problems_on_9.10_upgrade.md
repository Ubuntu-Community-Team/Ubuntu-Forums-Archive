---
title: "Nvidia problems on 9.10 upgrade"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by gizmobay on 2009-10-31
Don't know if anyone else saw this but I had a bit of a tricky time getting the nvidia drivers. I'm using a GeForce 5200 so I need the 173 drivers. The driver was working in 9.04 and I saw during the upgrade process that the 9.10 installed the kernel module for 173; however, when I logged in I was dumped back to terminal login. I tried doing a envyng -t and this didn't resolve the problem. I edited the xorg.conf and changed the driver from nvidia to nv as well as removed the glx modules section etc and I was able to login in low graphics mode. I then tried to use the gnome hardware driver setup to install the 173 drivers and it installed the driver but it still wouldn't work on boot. I changed the xorg.conf back to nv and removed the glx module section again and it logged in but on a reboot the settings were lost. I ended up logging into the command line I did a apt-cache search nvidia and removed all packages with nvidia and it also removed envygn. I then rebooted and it brought me back in low graphics mode without errors. I then opened up a terminal reinstalled envygn and did a sudo envygn -t and installed the nvidia drivers. I then rebooted and everything was working with the 173 drivers.

---

