---
title: "grub 0.97 problem on Karma"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by anthonie on 2009-11-22
Hello all!

I upgraded recently from 8.10 to 9.10, but had some other partitions for testing purposes around as well. 

Eveything went well, untill I decided that I wanted to clean up and remove the test partitions. I was not aware I had my grub installed on one of those. Hence: No boot.

So, naturally, I start a 9.10 liveCD, check that the devices are mounted and go to terminal to start grub. (I had to apt-get install it first.)

$anthonie sudo grub

grub> gives back (hd0,6)
grub> root (hd0,6)
grub> setup (hd0,6) 

(I chose hd0,6 so it would install it on the partition, rather tha  MBR but hd0 renders no results either but will give a non-fatal error)

grub> quit

For some reason, no new menu.lst has been created.

I have done this task numerous times but now on reboot I get a grub prompt.

I will post the output of fdisk -l below

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a680a67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78140128+   7  HPFS/NTFS
/dev/sda2            9729       11003    10241406    7  HPFS/NTFS
/dev/sda3           11005       19457    67898722+   f  W95 Ext'd (LBA)
/dev/sda5           11005       11514     4096543+  82  Linux swap / Solaris
/dev/sda6           13258       13379      979933+  82  Linux swap / Solaris
/dev/sda7   *       13380       19457    48821503+  83  Linux
ubuntu@ubuntu:~$ 

I am in doubt whether to install grub2 or try and fix the legacy grub, hopefully with the help of some people here on the board.

Kind regards,
Anthonie

---

### Post by kansasnoob on 2009-11-22
Please follow the steps in this tutorial:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

And post the output of the Boot Info Script in code tags here.

---

### Post by anthonie on 2009-11-22
Thanks for the reply. I decided to take the leap and change the grub legacy to grub-pc, which worked without any problem whatsoever.

The threat you pointed me to was new for me, so big thanks for that. Very usefull script there!

---

