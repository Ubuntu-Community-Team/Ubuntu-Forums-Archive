---
title: "How to find Ubuntu"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by phil66 on 2009-05-22
Windows XP
Ubuntu Hardy

80gb sata hard drive
250 gb sata hard drive

Ubuntu Hardy installed on 80gb hard drive
Windows Xp on 250 gb hard drive

Computer was dual booting using grub.
Lost Windows XP sent to shop for sata reinstall
Up returning I no longer have a grub boot screen
I do not know whether Ubuntu is still on the 80 gb hard drive

Have live cd of Ubuntu Hardy

How do I find Ubuntu and install grub boot manager

---

### Post by Tibuda on 2009-05-22
Boot your LiveCD and try to find the Ubuntu partition. If you can find it, you can reinstall GRUB following these instructions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by raymondh on 2009-05-22
Using liveCD , navigate to system > administration > partition editor (which is gparted).  You can use gparted to look into your harddrive and give you a visual output.

If you still have ubuntu in there (am thinking the shop deleted it but am hoping not) ... you can use supergrubdisk to reinstall grub

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

If Ubuntu is gone, you can re-install and GRUB will be installed as well.

Good luck.  Regards,

---

### Post by ALIENDUDE5300 on 2009-05-22
you can check if ubuntu is still installed with a tool like gparted. GRUB can be reinstalled with a live cd.

---

### Post by gooligan on 2009-05-22
As suggested, boot with live cd Then do the following (assuming /dev/sda is your hard disk drive)

```

sudo fdisk -l /dev/sda

```

If you find a partition with "System" column as Linux, you probably have Ubuntu still. You just have to reinstall grub.

---

### Post by phil66 on 2009-05-23
Thanks to all that replied to this posting.

Good news used gparted and found Hardy still on hard drive.

Installed grub and set the windows root in menu.lst

Both o/s's now working from grub.

The help was much appreciated):P

Ray

---

