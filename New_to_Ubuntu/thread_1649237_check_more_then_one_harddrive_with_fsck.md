---
title: "check more then one harddrive with fsck"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-12-19
how do i run fsck on my drives? all are ext2 power went out.

$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a732a72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156289024   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1f25

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d0647

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488385536   83  Linux

/dev/sda1 / #root
/dev/sdb1 /home/1tb #another hard drive mounted in home
/dev/sdc1 /home/500gb #another hard drive mounted in home

---

### Post by oldfred on 2010-12-20
From liveCD so everything is unmounted, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

Run each sda1, sdb1 & sdc1. With large drives it may take a while especially if ext2. You should think about ext4 for large partition. Also your system will perform a little better with a system partition that is 20-25GB and separate /home and/or /data.

---

