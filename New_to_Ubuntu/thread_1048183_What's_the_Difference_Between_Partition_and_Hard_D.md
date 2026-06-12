---
title: "What's the Difference Between Partition and Hard Drive?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by matey3 on 2009-01-23
As a an old DOS user and a new Linux user I am used to having different drives with different letters (ie A:, C:. F: etc.) But I like the concept in Linux a lot better because it makes more sense.
BUT recently I did something to my Linux box and I lost my second Hard Drive which had Vista loaded in it,??

Now when I do an fdisk -l I see a lot of partitions like sdb1, sdb2 etc. But I cannot see any of them which has FAT32 on it and I am confused if these things I see are partition on a single hard drive OR they are partitions on 2 or more hard drives?

Basically How would I distinguish between a partitions and the hard drives in Linux / Ubuntu? 

Thank You!

---

### Post by Bachstelze on 2009-01-23
sdb1 and sdb2 are on the same hard drive (sdb). Partitions on other drives will be like sda1, sdc2, sdi3, etc.

---

### Post by inclusivedisjunction on 2009-01-23
Partitions are divisions of a hard drive. Windows displays partitions as "drives" because in most usage with Windows, a drive would have only one partition.

In Linux, partitions can be easily distinguished from the entire drive. A drive will be at /dev/sda, /dev/sdb/ /dev/sdc, etc.... Partitions will be composed of a number following the drive identifier, for instance /dev/sda1, /dev/sdb2, etc...

---

### Post by SunnyRabbiera on 2009-01-23
well if you still had vista it would come up as NTFS instead of FAT, FAT is old hack and pretty much obsolete.
Now as for partition vs hard drive, well in linux we have a way to separate the two.
Internal drives are usually listed as sda
and extra drives are usually listed as sdb
so your CD player, your external drive are listed as extra media.
Your Sda drives are what you have in your computer, in a single boot Ubuntu is usually sda1, or even sda0
extras are usually listed as sda5 or something, during a dual boot ubuntu is usually sda5 or something

---

### Post by Bachstelze on 2009-01-23
Wrong, wrong, wrong, wrong!

> **SunnyRabbiera said:**
> 
Internal drives are usually listed as sda
and extra drives are usually listed as sdb

sda is the first drive and sdb is the second drive. That's all there is to it. Whether they are internal or external is absolutely irrelevant.

> **SunnyRabbiera said:**
> or even sda0

You will never **ever** see such a thing as sda0.

---

### Post by billgoldberg on 2009-01-23
> **matey3 said:**
> As a an old DOS user and a new Linux user I am used to having different drives with different letters (ie A:, C:. F: etc.) But I like the concept in Linux a lot better because it makes more sense.
BUT recently I did something to my Linux box and I lost my second Hard Drive which had Vista loaded in it,??

Now when I do an fdisk -l I see a lot of partitions like sdb1, sdb2 etc. But I cannot see any of them which has FAT32 on it and I am confused if these things I see are partition on a single hard drive OR they are partitions on 2 or more hard drives?

Basically How would I distinguish between a partitions and the hard drives in Linux / Ubuntu? 

Thank You!

When you use "sudo fdisk -l", there should be a "system" mentioning next to each parition/drive. 

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25019   200965086   83  **Linux**
/dev/sda2   *       25020       30119    40965750    7  **HPFS/NTFS**
/dev/sda3           30120       30401     2265165   82  **Linux swap / Solaris**

Because of the **hpfs/ntfs** label I know sda2 is my Windows partition.

As you see here all the partitions are on the same hard drive (they are all on sda).

Should you see /dev/sdb1 and /dev/sdb2 then you would know that those two partitions are on the second hard drive (sdb).

However you could always use the program "gparted" to look up such information as well.

---

### Post by matey3 on 2009-01-23
Thank you ALL very much, very good info. indeed.

---

### Post by meindian523 on 2009-01-23
<please ignore>bad post :(

---

### Post by gyaneshwar on 2009-01-23
Also you can check if you lost ntfs-3g package or it go corrupted. 
I do not know about Vista NTFS but with new ntfs-3g XP is working in read and write mode without any problems (so far :) )

---

