---
title: "Problem with grub"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by shadowber on 2010-04-26
I just installed xp on a second partition on the hard drive, and now the computer boots straight into windows without going through grub. How do I fix it? (I cannot access my ubuntu at all)

---

### Post by cak3 on 2010-04-26
Windows always writes its own bootloader to the MBR of the first HDD, which overrides GRUB.

The process to restore grub is different for Grub 1 and grub 2. If you are using a a pre-karmic (9.10) version, grub 1 should be the default.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) is a pretty detailed, if messy, guide to restoring grub.

[http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html](http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html) is cleaner, and is for grub 2.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) is a good guide for restoring legacy grub (grub 1).


Hope this helps.

---

### Post by shadowber on 2010-04-27
Thanks for the help... I fixed it but it took alot of tinkering... it would be nice if some1 simplified it for the beginners....

---

