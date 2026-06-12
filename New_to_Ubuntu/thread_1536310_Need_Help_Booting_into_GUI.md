---
title: "Need Help Booting into GUI"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by tbase on 2010-07-22
I was messing with my video drivers and XORG and I apparently screwed something up, as Ubuntu will now only boot into Terminal. Does anyone know how I might be able to fix this and get back into the GUI?

---

### Post by nothingspecial on 2010-07-22
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot

---

### Post by jtarin on 2010-07-22
Reboot and select recovery mode in GRUB for the latest kernel, then FailsafeX at the login screen, and then select low graphics mode.

---

### Post by SDerksen on 2010-07-22
Maybe you just got to press CTRL+ATL+F7
I had that problem once too.

---

