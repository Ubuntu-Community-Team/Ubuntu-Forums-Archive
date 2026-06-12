---
title: "Grub won't show Ubuntu"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by tyer22 on 2010-07-24
I have two drives 1 for my XP OS and an external drive for Ubuntu. It all boots fine until i get to the choose either XP or Ubuntu to boot. When i select Ubuntu it brings up the GRUB menu but the only 2 choices in the GRUB menu are Windows NT/2000/XP and Windows XP professional. Is there any way to have it show Ubuntu as a menu option. Also is there any way that I can just bypass GRUB all together and just run Ubuntu when i select Ubuntu from the Boot OS screen?

---

### Post by linux18 on 2010-07-24
boot off a livecd and:```
 sudo grub-install /dev/sda && sudo update-grub && sudo grub-install /dev/sdb && sudo update-grub  
```
that should get you into ubuntu

---

### Post by tyer22 on 2010-07-24
I tried it and it gives me the error

/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$

---

### Post by linux18 on 2010-07-24
type " sudo mount -a " the filesystem must not have auto-mounted on startup, this will fix that. then run:

  
sudo grub-install /dev/sda && sudo update-grub && sudo grub-install /dev/sdb && sudo update-grub

---

