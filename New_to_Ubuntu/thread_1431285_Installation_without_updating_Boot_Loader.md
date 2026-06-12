---
title: "Installation without updating Boot Loader"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by SeanMc98 on 2010-03-16
I have an existing multi-boot PC, with partitions for Windows/XP, openSUSE 11.2 (KDE) and Ubuntu 9.10 (Gnome).  The boot manager of my choice is openSUSE's GRUB.  I wish to reinstall Ubuntu 9.10, probably with KDE, into the existing Ubuntu partitions (delete and fresh install).  However, I do NOT wish to change the boot loader.

Using the LiveCD, I plan to use GParted to de-allocate the existing Ubuntu partions, and re-install.  How do I prevent the LiveCD install from updating the boot loader ?

The present boot loader has the following entry for Ubuntu:

```
###Don't change this comment - YaST2 identifier: Original name: none#
title Ubuntu 9.10 booting via symlinks
    root (hd0,7)
    kernel /vmlinuz root=/dev/disk/by-id/ata-WDC_WD2500BEVE-00WZT0_WD-WX11A10N3227-part8 ro quiet splash
    initrd /initrd.img

```This configuration is for a laptop.  I have a desktop with the Ubuntu GRUB boot loader, supporting multiple kernels.

---

### Post by lvleph on 2010-03-16
You can go through the normal installation, but right before you actually install click advanced and tell it not to install grub.

---

### Post by SeanMc98 on 2010-03-16
Thanks! I will do so today, and post back!

---

