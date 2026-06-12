---
title: "Cant get full screen"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by nvivek16 on 2011-05-11
I recently installed ubuntu 10.10 in my lap.After installation i was not able to get full screen.
Can anyone help with this problem

---

### Post by khelben1979 on 2011-05-11
It's because it's using open source video drivers for your pc hardware. Install the non-free drivers to fix this issue, or go for the Ubuntu 11.04 release instead to see if it works better.

You can start with typing: > lspci and then we know something more about your pc hardware and what's in there to know what type of graphic drivers you need to install.

---

### Post by seawolf167 on 2011-05-11
First thing to try is go to System -> Administration -> Hardware Drivers and install video drivers for your device. The reboot and adjust your resolution.

See if that works, else report back and we can try the proprietary drivers directly from the manufacturer.

---

