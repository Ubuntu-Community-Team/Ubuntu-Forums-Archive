---
title: "Different quantities of blocks by sfdisk"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by halfmind on 2010-09-02
Hello, All.  I installed 10.04 last week, and I've been reading up on partitioning. I was in "man sfdisk", and I thought I'd run the command with different flags, and got these results:

```
$ sudo sfdisk -s
/dev/sda:  78150744
total: 78150744 blocks
```

```
$ sudo sfdisk -Vl
Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   9355-   9356-  75146240   83  Linux
/dev/sda2       9355+   9729-    374-   3002369    5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       9355+   9729-    374-   3002368   82  Linux swap / Solaris
Warning: partition 1 does not end at a cylinder boundary
```

   As I understand it, /sda5 is a logical partition assigned to a primary partition, so I wasn't surprised that /sda2 and /sda5 have very nearly the same number of blocks. 
   For fun, I added the blocks in /sda1 and /sda2. Result: 78148609 blocks. Which, compared to the results of "sfdisk -s", is a difference of 2135 blocks. I'm just puzzled by it, that's all... Any thoughts?

---

### Post by srs5694 on 2010-09-02
Not every sector on the disk is allocated, for various reasons, which vary with the utility that laid out the partitions. For instance, some utilities start (and sometimes also end) partitions on particular boundaries (every 2048 sectors or on cylinder bounaries, for instance). This can leave some space unallocated at the start of the disk, at the end of the disk, and between partitions. It's theoretically possible to create an MBR disk with every sector but the first one (which is reserved for the MBR itself) allocated, but this sort of configuration is very rare.

---

### Post by halfmind on 2010-09-02
Thanks, srs5694. I'll mark it as, "Solved."

---

