---
title: "mount a hard drive without"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by cmaranhao on 2009-06-08
i want to mount that specific drive in my root but don't know how to do it.. maybe someone here can help me?

[http://img195.imageshack.us/my.php?image=96509387.png](http://img195.imageshack.us/my.php?image=96509387.png)

i formated my other drives and i already mounted all of them but i cannot do it to that specific drive (it has a lot of data and was not formatted!!!).

can someone help me?

when i input sudo fdisk-l it outputs the following:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73eee67d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9728    62782020    f  W95 Ext'd (LBA)
/dev/sda5            1913        3824    15358108+  83  Linux
/dev/sda6            3825        9728    47423848+  83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 17.3 GB, 17340000256 bytes
255 heads, 63 sectors/track, 2108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde65de65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         243     1951866   82  Linux swap / Solaris
/dev/sdc2             244        2108    14980612+  83  Linux

notice that sdb (my 200GB hard drive) is stated as an invalid partition table. can i mount the drive and recover the data? how?

i am not experienced in linux

---

### Post by Miljet on 2009-06-08
This is a duplicate. Please do not post duplicate threads. It will not help get your question answered any faster.

---

