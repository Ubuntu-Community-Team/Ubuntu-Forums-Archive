---
title: "Grub going to CLI"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Hamchan on 2009-03-27
I have a friend that rebuilt his computer while using the hard drives from his old computer. He used to dual boot XP and Red hat, with XP on the master and red hat on the slave. Now when he boots his computer, GRUB goes to a CLI instead of the familiar menu, but it didn't display XP.

What is really strange is that GRUB will display the menu when he has a usb flash drive plugged in. Does anyone know why this would happen?

Since he didn't ever use Red Hat we installed Ubuntu on the second hard drive, thinking that would reinstall Grub. GRUB still goes to the command line. When he has this flash drive plugged in, it gives him the menu complete with XP (though that won't load). 

Thank you in advance

---

### Post by James_Lochhead on 2009-03-27
It sounds like he installed GRUB on the flash disk...

try [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

with (hd0,0)

---

### Post by James_Lochhead on 2009-03-27
Also make sure the first hard disk is the first hard disk that appears in the boot order list in the BIOS. You can have the CD drive above it. However, I find if you have anything else above it, like an external hard disk (even one that isn't bootable), it doesn't ignore it and it try to boot to that.

---

