---
title: "baobob on single partition"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by brallan on 2010-05-09
baobob is a great utility for looking at use of space on a drive. Or is it? It allows searches within a part of the filesystem, but does not seem to allow selection of disks or partitions. Suppose I have an eeepc with 2 disks and an external USB drive:

sda1   (   4  GB)  mounted at    / 
sda2   (  16 GB)  mounted at    /home
sdb1   (500 GB)  mounted at    /media/externalUSB

Selecting by filesystem I can use baobab to look at the /home partition or the external drive, but as far as I can tell, there is NO way to use it to look at the / partition, precisely where I am most likely to need it, since it is by far the smallest partition.

Anyone know of a similar utility which does this?

---

### Post by Paqman on 2010-05-10
Every partition has a mount point within the filesystem. So just point Baobab at that folder and scan away.

---

### Post by brallan on 2010-05-11
> **Paqman said:**
> Every partition has a mount point within the filesystem. So just point Baobab at that folder and scan away.

That is exactly the problem. I cannot find a way to scan the partition mounted at / without scanning the other mount points as well.

---

### Post by brallan on 2010-10-11
bump

---

### Post by migs73 on 2010-10-11
Are you using it from a CD or is it an App on your OS?
IIRC you cannot mount the partition you are using i.e. your OS on /.
That is why most partition editors are also available as bootable discs, thus letting you mount all the partitions on your HDD.

---

### Post by mcduck on 2010-10-11
Just select Edit/Preferences and exclude every other file system than your /. Then use the "Scan filesystem" button. :)

---

