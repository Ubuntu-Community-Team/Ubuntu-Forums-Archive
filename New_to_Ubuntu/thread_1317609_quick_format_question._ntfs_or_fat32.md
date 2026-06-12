---
title: "quick format question. ntfs or fat32?"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by jarongg on 2009-11-06
so i want to do a dual boot of ubuntu and xp on my desktop. which files system should i format it to so that they will both play nice?

---

### Post by aPaSv5 on 2009-11-06
If I understand your question correctly, you choose to dual boot Windows and Linux, in which case the typical route is to partition your hard drive into three -- one partition, probably NTFS, for Windows, another as either ext3 or ext4 for Linux, and a third, much smaller partition formated as swap.

Note that you would not create the NTFS (or FAT or whatever else) partition for Windows if you already have it installed; just shrink the Windows partition you have now and make two new ones, as stated before. The Linux and Windows partitions should probably be of about equal size, and the swap partition should be as large as however much RAM you have.

There's probably some de-facto article about partitioning somewhere out there, but I don't know what it is.

Remember that Google is your friend.

---

### Post by aPaSv5 on 2009-11-06
Note that if you create your Linux partition as anything but, say, NTFS or FAT, you won't be able to access it in Windows, but I'm pretty sure that Linux can mount both NTFS and FAT partitions.

---

### Post by jarongg on 2009-11-06
dang. forgot about swap. well it's already formated as ntfs. after i partition it, and after i get xp installed, will the ubuntu installer format it as ext3 or do i need to do that as well?

---

### Post by ad_267 on 2009-11-06
I think you might also want an extra partition to share data between the two operating systems, and that could either be NTFS or Fat32.

I would suggest NTFS as although it's a Microsoft secret, support has been pretty well reverse engineered for Linux and it has a lot more features than FAT.

---

### Post by Sef on 2009-11-07
You can download some software from the repositories, so Ubuntu can read and write to the NTFS partition.  It is more stable than fat32.

---

