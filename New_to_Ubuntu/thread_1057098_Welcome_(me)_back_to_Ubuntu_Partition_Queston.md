---
title: "Welcome (me) back to Ubuntu Partition Queston"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-01
Hello!

After a 3 year Hiatus from Ubuntu...I'm happily back and this time for good :D


I'm having a bit of partition difficulty, Allthough I will be using Ubuntu as my daily workhorse, I still need Windows for some things I just can't do otherwise.

So, I need to adjust the partitions on my hard drive so I can install (BOOOO) windows on the 2nd partition.

Here is my current partition layout....

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18c6d85c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      915704      457821   83  Linux
/dev/sda2          915705   156296384    77690340    5  Extended
/dev/sda5          915768     2040254      562243+  83  Linux
/dev/sda6       150625503   156296384     2835441   82  Linux swap / Solaris
/dev/sda7         2040318   144954494    71457088+  83  Linux
/dev/sda8       144954558   150625439     2835441   82  Linux swap / Solaris


I want about 40GB for windows and the rest for Linux.

Can someone help guide me on what I need to do here.  The FILE SYSTEM resides on /dev/sda2 I believe.

Thanks !

---

### Post by Rinzwind on 2009-02-01
On the 2nd partition of a disc? I do not think you can use Windows XP without putting it at the beginning of your discs (ie.. 1st partition of a disc). Can you?? Wait for someone else to confirm this :)

Question: for wat do you need Windows XP. Based on your answer you can...

1. use VirualBox: install Windows inside your Linux install. AFAITested it works brilliantly. Plus you have 1 system to boot and when gnome started you click the BV ikon and start Win XP.

2. VMWare. You can nowadays use a lot of Windows directly in Linux with VMWare. It's a big portion of software and sometimes difficult but it has an install inside add/remove programs.

Otherwise you might need to re-install your whole machine :+
(do not start this w/o having my 1st Q answered!

---

### Post by handydan918 on 2009-02-01
What you want to do is possible, but more difficult than needs be. Windows likes to be on the first partition of the first HD, and if it is, everything else is pretty easy. 
I would consider a backup and reinstall...

---

### Post by jerome1232 on 2009-02-01
/dev/sda2 is an extended partition, so it is just a holder for those logical partitions (/dev/sda5, sda6, sda7, and sda8) nothing but other partitions reside on /dev/sda2.


Windows doesn't have to be the first disc but it does have to be a primary partition!

So you will need to shrink the partitions inside /dev/sda2 and shrink /dev/sda2 until you have enough room to toss a windows partition down after the logical partition. (the new partition would be /dev/sda3).

A screenshot from gparted would help visualize it better.

---

### Post by mistypotato on 2009-02-01
Thanks!

I tried to install gparted but for some some reason it's not available on my menu(s) even though in Package Manager it shows installed?

Help ?


(Do I HAVE to install the Gnome Desktop Environment for it to work or appear?)

---

