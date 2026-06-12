---
title: "i discovered something that concerns me"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by robgraves on 2011-05-07
i ran the fsck -l command, output here:

```
robgraves@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1977e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       25680   206062592    7  HPFS/NTFS
/dev/sda3           25680       57914   258922496    5  Extended
/dev/sda4           57927       60789    22987776    7  HPFS/NTFS
/dev/sda5           36136       56844   166339584   83  Linux
/dev/sda6           56870       57914     8388608   82  Linux swap / Solaris
/dev/sda7           25692       36136    83886080   83  Linux

Partition table entries are not in disk order
robgraves@ubuntu:~$ 
```what concerns me is this portion:

```
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
```

This, i believe, is the boot partition that windows had setup on my hard drive long before i ever did anything to it, as windows 7 came pre-installed on my computer.
   
Is partition 1 not ending on a cylinder boundary a reason for concern? 

How did that occur? 

And if it is a concern, what is the easiest way to fix this?

Thanks in advance.

---

### Post by tgalati4 on 2011-05-07
No problem.  Partitions that end on a boundary are a little more efficient for read-ahead, caching algorithms.  GParted will normally create partitions that end on a cylinder boundary.

With Windows, who knows?

It's doubtful that you will be touching the Windows partition much while in Linux.  So it's just a warning and nothing to worry about.

---

### Post by robgraves on 2011-05-07
cool, thank you, i saw that and it had me worried.

---

### Post by srs5694 on 2011-05-08
Actually, the speed advantages of partitions ending on cylinder boundaries haven't applied for well over a decade. In fact, the cylinder/head/sector (CHS) geometries reported by today's hard disks are fictions created to keep the BIOS and other CHS-using tools happy; the actual physical layout of partitions on a disk bears little resemblance to what the disks report.

Partitioning tools today have moved to a new policy of aligning partitions on 1 MiB boundaries. This improves performance with certain types of modern storage device, including Advanced Format disks, SSDs, and some types of RAID arrays. (See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the topic of partition alignment on Advanced Format disks.) The latest versions of GParted now align partitions on 1 MiB boundaries by default, not on cylinder boundaries. This change was fairly recent, though (within the last year or two, although of course the version shipped with Ubuntu inevitably lags a bit).

The fdisk warning about a partition not ending on a cylinder boundary might have been relevant in the arly 1990s, and might even be relevant today if you were running a very old version of DOS; but for most users it's irrelevant. If you've got a disk that uses a technology that works best with a power-of-2 4 KiB to 1 MiB alignment, you must examine the *start sector* (not the starting or ending *cylinder*) and determine if the value is divisible by the appropriate number.

---

### Post by robgraves on 2011-05-08
> **srs5694 said:**
> Actually, the speed advantages of partitions ending on cylinder boundaries haven't applied for well over a decade. In fact, the cylinder/head/sector (CHS) geometries reported by today's hard disks are fictions created to keep the BIOS and other CHS-using tools happy; the actual physical layout of partitions on a disk bears little resemblance to what the disks report.

Partitioning tools today have moved to a new policy of aligning partitions on 1 MiB boundaries. This improves performance with certain types of modern storage device, including Advanced Format disks, SSDs, and some types of RAID arrays. (See [this article]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/") I wrote on the topic of partition alignment on Advanced Format disks.) The latest versions of GParted now align partitions on 1 MiB boundaries by default, not on cylinder boundaries. This change was fairly recent, though (within the last year or two, although of course the version shipped with Ubuntu inevitably lags a bit).

The fdisk warning about a partition not ending on a cylinder boundary might have been relevant in the arly 1990s, and might even be relevant today if you were running a very old version of DOS; but for most users it's irrelevant. If you've got a disk that uses a technology that works best with a power-of-2 4 KiB to 1 MiB alignment, you must examine the *start sector* (not the starting or ending *cylinder*) and determine if the value is divisible by the appropriate number.
:-s
you lost me a little, but i think you said its mostly irrelevant today, my pc is not even a year old yet.  very informative reply though

---

