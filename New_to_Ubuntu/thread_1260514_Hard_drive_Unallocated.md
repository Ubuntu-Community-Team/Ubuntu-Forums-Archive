---
title: "Hard drive Unallocated"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by Essary on 2009-09-07
======================
libparted : 1.8.8
======================
Invalid partition table - recursive partition on /dev/sda.


I installed a second HD and copied 100 Gb of data that I really, really don't want  to lose to this drive, all in windows XP. I then proceded with a fresh install of WinXP and Ubuntu. The new HD shows to be only unallocated space, and after installing Ubuntu and rebooting I get an error like "disk read error" in the boot process. 

First, is there a way to get my data back that I really, really don't want to lose, or is it gone forever?

Second, why am I getting this disk read error and how do I fix it. I am planning to repartition the drive and just start over again. 

I am very new to linux/ubuntu and am trying to get everything set up so I can get into linux more.

---

### Post by Ocxic on 2009-09-07
you could try testdisk(in the repos), it helps with recovering partitions and data, or you could see if you can access from a windows system since you copied the files from there.

---

### Post by Essary on 2009-09-08
testdisk did the trick, thank you. I can now access my files that I really, really didn't want to lose in windows and Ubuntu. However, when I look at the drive in gparted it shows that drive as unallocated space. I can still access the files/mount the drive. I should probably fix that somehow right?
 
For others with same problem:
In WinXp Setup there was nothing to distinguish one drive from another, they had the exact same info. I just unplugged the storage drive so I wouldn't accidentally install on it.
 
I switched the cables around on the drives. I had my OS drive on SATA 1 and the storage drive on SATA 2, according to my mobo. In Ubuntu they came up as *b and *a respectively, the opposite of how I assumed they would. I switched that around and it seemed to help windows, it made no diff to Ubuntu. Probably something I should learn about there.
 
Installed Ubuntu, no problems once you learn how to set up your partitions. Ran testdisk as suggested, learned how to use it, and fixed the partition table.
 
Being a fresh install of XP I had to enable large drive support. To get my storage drive working right I also had to install the drivers for the specific drive (Seagate Barracuda).
 
Everything "seems" to be working fine at this time. But there is still that problem with gparted thinking that my storage drive is unallocated, but still accessible.

---

