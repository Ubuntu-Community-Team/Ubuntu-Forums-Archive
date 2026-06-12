---
title: "Only allowed 4 primary paritions!"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Zanderist on 2011-03-29
I'm trying to create a media space where I can share music and photos between ubuntu and windows.

I've allocated some memory on the hard drive, but I can't do anything with it, to achieve what I want it to do.

So I'm thinking about getting rid of HP's recovery partition.

What should I do.

---

### Post by collisionystm on 2011-03-29
If you are using a newer version of ubuntu and depending on the ext file system you have, you can use gparted to resize your ubuntu partition and free up space. Then turn the free space into a fat32 or ntfs partition.

you can get gparted from the software center or synaptic and run it from system, administration

---

### Post by oldfred on 2011-03-29
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
The Hedge show grahically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Shared NTFS partition  - you can also use links.
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Mark Phelps on 2011-03-30
> **Zanderist said:**
> I'm trying to create a media space where I can share music and photos between ubuntu and windows.

I've allocated some memory on the hard drive, but I can't do anything with it, to achieve what I want it to do.

So I'm thinking about getting rid of HP's recovery partition.

What should I do.

oldfred already provided you some really good links to additional info ...

But to provide my response to your question about the recovery partition -- the answer depends on whether or not you will ever need to restore your PC to its original state.  If you know for sure the answer is NO, they you can remove the recovery partition; otherwise, you should keep it.

Also, if you're currently running Win7, go into the Backup feature and use the option to create and burn a Win7 Repair CD.  This could come in really handy later if you need to repair the Win7 boot loader.

---

### Post by Zanderist on 2011-03-30
I've figured out what to do.

Shrunk Ubuntu in the extended partition, then with that unallocated space with the extend partition I formatted it into ntfs.

I'm also getting rid of the recovery partition, but not before I made DVD copies of it.

---

