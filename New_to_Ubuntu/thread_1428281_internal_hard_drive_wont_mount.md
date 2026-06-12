---
title: "internal hard drive wont mount?"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by ttr398 on 2010-03-12
Hi there, not sure if this belongs here or in hardware, but:

Got a new internal HDD today and it wont mount, however ubuntu 'sees' it. 

Output of fdisk -l:

```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb2d8b2d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf05b62d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14945   120045681    7  HPFS/NTFS

```

interestingly ubuntu is calling it sda - it's the 250gb one.

ubuntu is installed on sdb. 

Assistance please! :D

---

### Post by sisco311 on 2010-03-12
You have to format the disk. Use [GParted]("apt://gparted") (click the apturl link to install it). It's in the repos.

---

### Post by coffeecat on 2010-03-12
Here's the problem:

> Disk /dev/sda doesn't contain a valid partition table

No brand-new bare HD does.

Install Gparted as sisco311 says, and then (in Gparted) Device > Create Partition Table. Make sure you are showing the correct disc in the drop down box top-right. You don't want to be creating a partition table in one of the other discs. Once you have a partition table you can create whatever partitions you need.

Ubuntu needs formatted partitions to mount, and partitions need a partition table.

---

