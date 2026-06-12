---
title: "Botched Server Raid1 Install  --HELP"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by chuckval on 2011-02-20
Trying to replace a failing Netware 4.11 Server w/Ubuntu.  Having only a little Windoze experience I'm struggling mightly.    I have my server up and running but it looks like I botched the Raid1 setup (small wonder).  The command line setup is tough for a newub.  I was able to find a way to query the Raid status as noted below.   Can anyone give me a step by step procedure to fix this ?

Thanks,  Chuck
=====================================================


Disk /dev/sdb: 18.4 GB, 18351959040 bytes
64 heads, 32 sectors/track, 17501 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005fc06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243      248816   fd  Linux raid autodetect
/dev/sdb2             244       17501    17672177    f  W95 Ext'd (LBA)
/dev/sdb5             244       17501    17672176   fd  Linux raid autodetect

Disk /dev/sda: 18.4 GB, 18351959040 bytes
64 heads, 32 sectors/track, 17501 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cfdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2         244      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             245       17501    17670145    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             246       17501    17670144   8e  Linux LVM

Disk /dev/md1: 18.1 GB, 18096193536 bytes
2 heads, 4 sectors/track, 4418016 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

---

