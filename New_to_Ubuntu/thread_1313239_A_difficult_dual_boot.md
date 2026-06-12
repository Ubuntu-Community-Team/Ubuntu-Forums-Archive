---
title: "A difficult dual boot"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by pgar23 on 2009-11-03
Hi community,

    I am having a dual boot system (Ubuntu 9.10 and Windows 7. I have installed in this order;  Ubuntu first (because I had it already installed and didnt want to back up and re-install everything) then Windows 7.

I know that when you install Windows after Ubuntu that the MBR overwrites the GRUB. Now when I turn my laptop on, it boots directly into Windows 7.

MY QUESTION: How do I re-install GRUB menu and have both options, WIndows and Ubuntu?

My partitions:
```

python@python-laptop:~$ sudo fdisk -l
[sudo] password for python: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f9a64c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19307   155083446   83  Linux
/dev/sda2   *       19308       19320      102400    7  HPFS/NTFS
/dev/sda3           19320       29164    79073280    7  HPFS/NTFS
/dev/sda4           29165       30401     9936202+   5  Extended
/dev/sda5           29165       29434     2168743+  82  Linux swap / Solaris
/dev/sda6           29435       30401     7767396   83  Linux
python@python-laptop:~$ 

```

My /etc/grub.d Folder looks like this:

00_header  05_debian_theme  10_linux  20_memtest86+  30_os_prober 40_custom  README

I was thinking that I could add the custom lines to the 40_custom file, but how do I know which lines will boot Windows 7 (because there are 2 NTFS filesystems, one is bootable and one is not)?

If i need to add both of the /dev/sda2 and /dev/sda3, how do i go about adding that to the 40_custom file?

Thanks in advance, I know that this is a lot to read, but I like to be thorough.

---

### Post by ajgreeny on 2009-11-03
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) should tell you everything you need.  From what I've read it is not as simple as it was with legacy grub, but this thread tells you all about it, including how to restore grub2.

---

### Post by fo rizzle on 2009-11-03
Check out the super grub disk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)). There is an option to install grub to the MBR and autoconfigure it for Linux. Then, you boot, find menu.lst, and add the entry for windows!

---

### Post by kansasnoob on 2009-11-03
> **fo rizzle said:**
> Check out the super grub disk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)). There is an option to install grub to the MBR and autoconfigure it for Linux. Then, you boot, find menu.lst, and add the entry for windows!

There is no menu.lst in grub2.

---

### Post by fo rizzle on 2009-11-03
> **kansasnoob said:**
> There is no menu.lst in grub2.
Right... Oops... I meant grub.cfg... Or whatever it is now.

---

### Post by kansasnoob on 2009-11-03
The following instructions have worked for me:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

From your post:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f9a64c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19307   155083446   83  Linux
/dev/sda2   *       19308       19320      102400    7  HPFS/NTFS
/dev/sda3           19320       29164    79073280    7  HPFS/NTFS
/dev/sda4           29165       30401     9936202+   5  Extended
/dev/sda5           29165       29434     2168743+  82  Linux swap / Solaris
/dev/sda6           29435       30401     7767396   83  Linux
python@python-laptop:~$

I can't be certain whether sda1 or sda6 is Karmic /root. Just guessing by size I'd say sda6, but I can't be sure.

If you run the Boot Info Script from live CD as described here you can see more info about the partitions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

You shouldn't need to edit any files right now, just determine which partition to mount and chroot, then "grub-install /dev/sda" and "update-grub", then exit and unmount as explained.

---

### Post by Rhubarb on 2009-11-03
There's also the grub2 ubuntu wiki (which seems to be down at the moment for some odd reason):
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I recall that there's a grub app you can run called grub-probe (or similar) that can detect your windows and Ubuntu installs, then you can re-install grub2 with that updated information.

But unfortunately as the wiki is down, and I don't have a dual-boot install to play with, I can't be 100% sure that I'm right about this.

Just remember that Karmic by default uses Grub2, not grub legacy with new installs (ie not upgrades).  So it's probably best to stick with Grub2 to allow you to dual-boot.

---

