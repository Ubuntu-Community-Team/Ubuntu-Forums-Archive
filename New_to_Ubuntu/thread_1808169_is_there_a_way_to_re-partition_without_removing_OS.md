---
title: "is there a way to re-partition without removing OS"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by mushroom08 on 2011-07-20
Hi i have a new laptop with windows 7 i dont have the install cd's for it but would like to install kubuntu alongside it is there a way to re-partition my HD's free space without deleting window? (i want to keep windows for gaming) plz help](*,)

---

### Post by zombifier25 on 2011-07-20
1. You can install it using a USB. Also, the installer should let you repartition your hard drive for Kubuntu and leave Windows intact.

2. If you're still paranoid, use Wubi. It should allow you to install K/Ubuntu from Windows as if it is a Windows program.

---

### Post by mushroom08 on 2011-07-20
thank you just was not sure if i could

---

### Post by bigpayne69 on 2011-07-20
You might want to defrag Windows first. If not, you could lose some of your data when you partition your drive.

---

### Post by mastablasta on 2011-07-20
> **bigpayne69 said:**
> You might want to defrag Windows first. If not, you could lose some of your data when you partition your drive.
 
+1 
 
try to make recovery disks for windows (even if oyu dont' have install they might come in handy later on if needed),
 
Otherwise you need to defragment the drive at least 2 times to avoid data loss (second time it will be faster)
 
after that is done you can use windows disk manager to create an empty disk space, then all you need to do is install Ubuntu to largest empty disk space.
 
if you just want to try out the system then Wubi (it installs Ubuntu within windows in a virtual file) is a much safer way.

---

### Post by Bucky Ball on 2011-07-20
Defrag the Windows partition several times before shrinking the partition. Power Defragmenter is better than the default one. Shrink the partition using Windows software, *not* Gparted. Leave the rest free space (don't make partitions for Ubuntu with Windows). Without defrag there is a risk of losing data but also you will get inaccurate indication of how much space is used/unused on the partition before defrag (as Windows spits data all over the partition). 

When you install Ubuntu, choose 'Something else' or 'Manual Partitioning' when you get to the partitioning section. Leave the Windows install alone (it will be there, clearly visible, as NTFS partition). Create the Ubuntu partitions in the free space. Advisable is:

/ = where the OS is (20Gb max)
/home = where your personal data and settings are (large as you want)
/swap (double your RAM size, although this is an ongoing debate)

All of these mount points are defaults you can simply click to choose in the partitioner.

---

### Post by mastablasta on 2011-07-20
> **Bucky Ball said:**
> When you install Ubuntu, choose 'Something else' or 'Manual Partitioning' when you get to the partitioning section. Leave the Windows install alone (it will be there, clearly visible, as NTFS partition). Create the Ubuntu partitions in the free space. Advisable is:
 
/ = where the OS is (20Gb max)
/home = where your personal data and settings are (large as you want)
/swap (double your RAM size, although this is an ongoing debate)
 
All of these mount points are defaults you can simply click to choose in the partitioner.
 
this is advanced partitioning. and it's not necessary for newcommer for 2 reasons:
1. the Ubuntu installer partitions the disk automaticly.
2. you can always create additional partitions later if necessary. for example swap is needed only if you use hibernation and to increase perofmance (it's created automaticly), /home is only needed if you want you data and programme settings to be separate from the OS (kind of like having *My documents* folder on another disk). again this is not necessary and is even not cretaed with default install options. though it's a good idea later on. but then again i have 2 maschines and neither has /home on separated partition.
 
why complicate things on start?

---

### Post by Bucky Ball on 2011-07-20
Not complicated but each to their own. Having a /home partition to start with is a lot easier than creating one and trying to move things to it later.

Ubuntu doesn't partition the disks the way I want to *ever*. I *never* use auto-partitioning. But as I say, each to their own and it's up to OP. ;)

PS: Auto-install with 11.04, if that is what is being installed? Wouldn't trust it. Wubi? Designed for trying Ubuntu and installing from Wubi to hard drive can be notoriously problematic.

---

### Post by mushroom08 on 2011-07-26
been a long week at work but thanx all for the advice^^

---

