---
title: "Partitions not listed in /dev"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by bethebunny on 2010-05-30
I have two 1.5TB drives, each with large ex3 partitions on which I have a lot of large data stored (home movies, etc), and a third 500GB drive on which I have my bootable operating systems. Both of my larger drives have become unmountable. More specifically, their partitions are not even listed in /dev.

The following commands were all run from an Ubuntu 10.04 x86_64 live cd.

```
ubuntu@ubuntu:~$ ls /dev | grep sd
sda
sdb
sdc
sdc1
sdc2
sdc3
sdc4
sdc5
sdc6

```

However, the partitions are still there, even listed in the partition tables.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00074752

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      179402  1441046533+  83  Linux
/dev/sda2          179403      180945    12394147+  83  Linux
/dev/sda3          180946      182401    11695320    f  W95 Ext'd (LBA)
/dev/sda5          180946      182401    11695288+  82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f06d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6566    52740096    7  HPFS/NTFS
/dev/sdb2            6567      182401  1412394637+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066fa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3958    31792603+  83  Linux
/dev/sdc2            3959       28158   194386500   83  Linux
/dev/sdc3   *       28159       53303   201975808    7  HPFS/NTFS
/dev/sdc4           54643       60801    49472167+   5  Extended
/dev/sdc5           54643       60518    47198938+   7  HPFS/NTFS
/dev/sdc6           60519       60801     2273166   82  Linux swap / Solaris

```

Gparted sees the partitions also, and recommends fixing them with e2fsck, but when I ask it to, it fails with 'e2fsck: No such file or directory while trying to open /dev/sda1', which is pretty clearly caused by Gparted simply attempting to naively use the /dev entry which isn't there.

Attempting to manually use fsck.ext3 is meeting with only frustration:


```
ubuntu@ubuntu:~$ sudo fsck.ext3 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext3: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck.ext3 -b 0 -B 4096 /dev/sda
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext3: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

```

This is when run on a fresh-booted live cd, where nothing has attempted to mount anything; /dev/sda isn't in the mtab, or in blkid.

I've tried running TestDisk, and even used it to rewrite the partition table on /dev/sda, which hasn't changed any of these results.

Worst case scenario I could purchase a large external drive and use TestDisk to dump data onto it, but that would be an expensive and laborious process.

I think I'd be fine if I could just get /dev to list the partitions of sda and sdb to run fsck on them. Any idea why they're not showing up, what I could do to get them to appear, or other ideas to get these partitions to a mountable state?

---

### Post by bethebunny on 2010-06-16
I still don't know exactly what the problem is; somehow it is related to udev and the device file name rules. Regardless, a default Gentoo install does not have this problem; I guess this is goodbye to Ubuntu, for now.

---

