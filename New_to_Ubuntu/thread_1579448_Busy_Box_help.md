---
title: "Busy Box help"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by zharless92 on 2010-09-21
After i dualbooted linux onto my pc that had windows xp, when booting into ubuntu it says "Gave up waiting for root device" and then opens up a BusyBox v1.13.3. I've installed ubuntu multiple times on a pc and have never seen this error. But even if i reinstall ubuntu i still get this error.

---

### Post by jtarin on 2010-09-21
Is this a regualr install or a WUBI install?

---

### Post by zharless92 on 2010-09-21
It was a regular install.

---

### Post by zharless92 on 2010-09-21
If i press 'e' when the boot menu pops up and delete the 'search' line and then change 'linux.......root=' to 'root=/dev/sda5' and it boots fine but idk how to save that.

---

### Post by jtarin on 2010-09-22
Try running sudo update-grub from the desktop.

---

### Post by zharless92 on 2010-09-22
I've tried. But as soon as I reboot it goes back to the way it was.

---

### Post by jtarin on 2010-09-22
> **zharless92 said:**
> I've tried. But as soon as I reboot it goes back to the way it was.
[Go Here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") and use method 3 chroot. I'm assuming Grub is in your MBR?

---

