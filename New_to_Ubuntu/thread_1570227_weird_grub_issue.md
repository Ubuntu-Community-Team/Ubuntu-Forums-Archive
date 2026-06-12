---
title: "weird grub issue"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by olayak on 2010-09-07
so on dev/sda1 I have win 7 (for backup reasons only).
and my grub says that on dev/sda7 I have the good, working kernel version of ubuntu.

however, before these two, there are about 6 other kernel versions (none of which are listed as active in synaptic manager) and it doesn't say which sda they are on.  these versions are broken.  (they have bugs when i try to get them to work).

how can I quickly and easily remove all these crap versions?  One potential problem - 
one of the crap versions (on unknown sda) has the same kernel number as the good, working version of ubuntu on sda7!

please help!
thanks
Kathy

---

### Post by grief -l on 2010-09-07
You can use synaptic to remove them, but I wouldn't mess with the one that's the same ver as your working version -you could end up empty!

Or if they really are on their own partitions you can use cfdisk or GParted to delete those partitions (read the man pages carefully before tackling it)

---

### Post by wojox on 2010-09-07
What does this command tell us?

```
sudo fdisk -l
```

---

### Post by olayak on 2010-09-07
> **wojox said:**
> What does this command tell us?

```
sudo fdisk -l
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x935d59dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11418    91709835    7  HPFS/NTFS
/dev/sda2           11418       30401   152484545+   5  Extended
/dev/sda5           17520       30030   100494576   83  Linux
/dev/sda6           30031       30401     2980026   82  Linux swap / Solaris
/dev/sda7           11418       17264    46958592   83  Linux
/dev/sda8           17264       17519     2050048   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 3965 MB, 3965190144 bytes
122 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7564 * 512 = 3872768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      426146      458759   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(426145, 96, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(458758, 19, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       57228      159778   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(57227, 98, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(159777, 27, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      247166      500899   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(247165, 104, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(500898, 2, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      351212      352313     4161592    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(351211, 117, 39)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(352312, 40, 32)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by olayak on 2010-09-07
> **grief -l said:**
> You can use synaptic to remove them, but I wouldn't mess with the one that's the same ver as your working version -you could end up empty!

Or if they really are on their own partitions you can use cfdisk or GParted to delete those partitions (read the man pages carefully before tackling it)

I think they are on their own partitions, cause synaptic doesn't recognize them if I am in sda7!  I would use gparted, but I'm not sure what partition they are on!

---

