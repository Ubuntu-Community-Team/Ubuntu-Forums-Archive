---
title: "Grub Help"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by 10up on 2010-11-01
I recently decided to reformat and switch the partitions I had my ubuntu and windows booting from.  Also upgraded to Windows 7 and Ubuntu 10.10

I installed windows 7 first and ubuntu second.  After installing ubuntu my computer boots directly into it.  I've downloaded and burned SuperGrub but it only detects the linux partitions as well.

here is my output from & sudo fdisk -l




```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19365   155547648    7  HPFS/NTFS
/dev/sda2   *       19366       22567    25719117+  83  Linux
/dev/sda3           37593       38089     3992122    5  Extended
/dev/sda4           22568       37592   120688312+   b  W95 FAT32
/dev/sda5           37593       38089     3992121   82  Linux swap / Solaris

Partition table entries are not in disk order
```

Any ideas on why it doesn't recognize the Windows?

---

### Post by mahendrachhetri on 2010-11-01
hi there all!

help needed urgently

i cannot booot into windows after installing ubuntu 10.10

can any one help me to recover my windows 7.

---

