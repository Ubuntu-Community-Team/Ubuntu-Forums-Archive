---
title: "Partimage backup process"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Altadena on 2009-09-26
I am new to Ubuntu, and after have installed and configured my system for my initial needs, I would like to make images of the system partitions to keep a snapshot of this initial configuration just in case I need to restart form this base configuration.

I installed Ubuntu 9.0.4 on a system with 2 hard disks (see below). The first disk had Windows XP installed on it, so I decided to dedicate all disk 'b' to Ubuntu. The MBR I believe is still on disk 'a' to allow for dual boot.

The *fdisk -l *output is listed below:

```

Disk /dev/sda: 8455 MB, 8455200768 bytes
240 heads, 63 sectors/track, 1092 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa7c2a7c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1091     8247928+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf841f841

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4834    38829073+  8e  Linux LVM
/dev/sdb2            4835        4865      249007+   5  Extended
/dev/sdb5            4835        4865      248976   83  Linux


```The confusion started when I looked at GParted and with my surprise I found 2 additional devices (the first 2 in the list of devices in GParted):

```

/dev/mapper/alice-root
/dev/mapper/alice-swap_1
/dev/sda
/dev/sdb

```So here are my questions:

1) I don't understand how */dev/mapper/alice-root* and */dev/mapper/alice-swap_1* relate to the partitions of sda and sdb;

2) what are the partitions that I need to back up with Partimage if I want to rebuild my system from scratch?

Thank you for your help

---

