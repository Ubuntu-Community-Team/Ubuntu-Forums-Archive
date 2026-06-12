---
title: "NVIDIA drivers problem"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by risingpowers on 2009-01-11
I tried to install the 180.22 NVIDIA driver and it seemed to install correctly, but when my PC rebooted I had to start it in safe mode or low graphics mode. I can't adjust my screen resolution higher than 1280 x 1024 or use effects. I went back to using the 177 drivers recommended by Hardware Drivers, but the problem persists. Help? My graphics card is an 8800GT if that's relevant.

---

### Post by Bachstelze on 2009-01-11
Did you try to use the nvidia installer? If so, you must remove the Ubuntu drivers first.

---

### Post by Bachstelze on 2009-01-11
Did you try to use the nvidia installer? If so, you must remove the Ubuntu drivers first.

---

### Post by risingpowers on 2009-01-11
> **HymnToLife said:**
> Did you try to use the nvidia installer? If so, you must remove the Ubuntu drivers first.

Aye, that must be it. How can I fix this now, though?

---

### Post by Xiong Chiamiov on 2009-01-11
Try logging into recovery mode, then running
```

sudo dpkg-reconfigure xorg-xserver

```
Also, take a look in /etc/X11 and see what files there are (as the driver installation probably make backups of xorg.conf.

---

### Post by risingpowers on 2009-01-11
> **Xiong Chiamiov said:**
> Try logging into recovery mode, then running
```

sudo dpkg-reconfigure xorg-xserver

```
Also, take a look in /etc/X11 and see what files there are (as the driver installation probably make backups of xorg.conf.

It did make backups, but they wouldn't load. I also ran that command in recovery mode and it did nothing.

---

### Post by Bachstelze on 2009-01-11
Firs, uninstall the drivers you manually installes:

```
sudo sh NVIDIIA-blahblahblah.sh --uninstall
```

Then uninstall your Ubuntu drivers and reinstall the NVIDIA ones.

---

### Post by risingpowers on 2009-01-11
Okay, so the display is working properly now, but I can't enable any desktop effects.

---

