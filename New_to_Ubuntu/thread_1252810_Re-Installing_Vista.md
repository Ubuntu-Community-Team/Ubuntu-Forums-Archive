---
title: "Re-Installing Vista"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by daniell59 on 2009-08-29
I may need to re-install Vista. When I try to re-boot into Vista I get a window that says it is updating. It never finishes. I tried a repair with DVD. The earlier set point did not help. If I re-install Vista, what will happen to my Ubuntu? The Ubuntu is on a different hard drive than the Vista. What about the GRUB?

Thanks in advance.

---

### Post by LewRockwell on 2009-08-29
After the Vista re-install you will need to reinstall the grub bootloader

IIRC, in one of your earlier threads Super Grub Disk was mentioned...or maybe we're mistaken...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by daniell59 on 2009-08-29
> **LewRockwell said:**
> After the Vista re-install you will need to reinstall the grub bootloader

IIRC, in one of your earlier threads Super Grub Disk was mentioned...or maybe we're mistaken...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

Thanks, I cannot seem to locate the download site for the Super Grub.
How does Super Grub differ from the ordinary Gurb?

---

### Post by inkrypted on 2009-08-29
Just reinstall Windows Vista and once that is done. 
Boot to live CD
Open terminal
type sudo grub
press enter
type find /boot/grub/stage1
press enter
type root (hd?,?) to find GRUB location
press enter
type setup (hd?) ? being the drive you found with the above command
then press enter
type quit
press enter
and reboot

And you will be back to normal.

---

### Post by tchoklat on 2009-08-29
Supergrub is a utility to allow you to boot your HDD. Grub is the bootloader that linux uses (some distos use lilo) to boot the distro. SuprGrub will rebuild your grub if it is broken ....

---

### Post by tchoklat on 2009-08-29
try this-
 
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

