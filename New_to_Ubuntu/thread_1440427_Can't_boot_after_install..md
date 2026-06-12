---
title: "Can't boot after install."
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Target25 on 2010-03-27
Here's my problem. I've notebook Asus with 250 Gb HDD (/dev/sda) with Windows XP onboard. And I want to setup Ubuntu on removable 20 Gb USB HDD (/dev/sdb). BIOS priority is CD-ROM, then Removable, then main HDD. During install process, Ubuntu informs that Grub will be installed to hd0. Because I don't know what is hd0 and how to distinguish between /dev/sda(/dev/sdb) and hd0, I've manually select /dev/sdb (and nice try both /dev/sdb1 and /dev/sdb5) 
Ubuntu doesn't want to boot, writin "Grub Read Error".
Is there a way to start Ubuntu?

---

### Post by s_ø on 2010-03-27
Hi. See this post about reinstalling grub. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by oldfred on 2010-03-27
We now have to ask what version since new installs of Karmic use grub2 and older installs and upgrades to Karmic used grub legacy (0.97).
The link above is for old grub.

If you want to reinstall:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you want to know what is installed where so we can give more specific recommendations:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by nitstorm on 2010-03-27
sda means the partitions that are present in your internal drive, for example sda1 means ur first partition on your internal drive
hd0 means your first hard-dsik

sdb means removable hard-drives, thumb drives and so on, basically stuff that can be plugged in and pulled out.

Everyone else pointed you out on repairing so just wanted you to know what sda, sdb and hd0 means

---

### Post by s_ø on 2010-03-27
grub uses hd0, hd1...
ubuntu uses sda, sdb ... for every type of harddisk.

---

