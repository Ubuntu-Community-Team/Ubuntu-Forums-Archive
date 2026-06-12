---
title: "How to expand root partition"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by madhavhmk on 2009-08-13
I am running out of space in my root partition and I would like to expand the volume byfreeing some space from windows partition.....and I am not able to do both....

here is the output of fdisk -l:

 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              10        1315    10485760    7  HPFS/NTFS
/dev/sda2   *        1315        9147    62914560    7  HPFS/NTFS
/dev/sda3            9148       19458    82815716    f  W95 Ext'd (LBA)
/dev/sda4   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda5            9148        9755     4883728+  83  Linux
/dev/sda6            9756       19130    75302912    7  HPFS/NTFS
/dev/sda7           19131       19458     2620416   dd  Unknown

and output of df -h: (presently on live cd)

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1009M   16M  994M   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                1009M   16M  994M   2% /lib/modules/2.6.24-16-generic/volatile
varrun               1009M  104K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   80K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
tmpfs                1009M   36K 1009M   1% /tmp
df: `/home/ubuntu/.gvfs': Transport endpoint is not connected
/dev/sda4             2.5G  633M  1.9G  25% /media/MEDIADIRECT
/dev/sda6              72G   60G   13G  84% /media/New Volume
/dev/sda1              10G  5.2G  4.9G  52% /media/RECOVERY
/dev/sda2              60G   56G  4.6G  93% /media/OS
/dev/sda5             4.6G  4.1G  259M  95% /media/disk



When I tried loading gparted, it is not listing the different partitions...instead, it is listing the entire HDD as a single partition...

So I am not able to make any changes....

please help me out ....thanks

---

### Post by madhavhmk on 2009-08-13
I am running out of space in my root partition and I would like to expand the volume byfreeing some space from windows partition.....and I am not able to do both....

here is the output of fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

Device Boot Start End Blocks Id System
/dev/sda1 10 1315 10485760 7 HPFS/NTFS
/dev/sda2 * 1315 9147 62914560 7 HPFS/NTFS
/dev/sda3 9148 19458 82815716 f W95 Ext'd (LBA)
/dev/sda4 * 19131 19458 2620416 c W95 FAT32 (LBA)
/dev/sda5 9148 9755 4883728+ 83 Linux
/dev/sda6 9756 19130 75302912 7 HPFS/NTFS
/dev/sda7 19131 19458 2620416 dd Unknown

and output of df -h: (presently on live cd)

Filesystem Size Used Avail Use% Mounted on
tmpfs 1009M 16M 994M 2% /lib/modules/2.6.24-16-generic/volatile
tmpfs 1009M 16M 994M 2% /lib/modules/2.6.24-16-generic/volatile
varrun 1009M 104K 1009M 1% /var/run
varlock 1009M 0 1009M 0% /var/lock
udev 1009M 80K 1009M 1% /dev
devshm 1009M 12K 1009M 1% /dev/shm
tmpfs 1009M 36K 1009M 1% /tmp
df: `/home/ubuntu/.gvfs': Transport endpoint is not connected
/dev/sda4 2.5G 633M 1.9G 25% /media/MEDIADIRECT
/dev/sda6 72G 60G 13G 84% /media/New Volume
/dev/sda1 10G 5.2G 4.9G 52% /media/RECOVERY
/dev/sda2 60G 56G 4.6G 93% /media/OS
/dev/sda5 4.6G 4.1G 259M 95% /media/disk



When I tried loading gparted, it is not listing the different partitions...instead, it is listing the entire HDD as a single partition...

So I am not able to make any changes....

please help me out ....thanks

---

### Post by madhavhmk on 2009-08-13
I am running out of space in my root partition and I would like to expand the volume byfreeing some space from windows partition.....and I am not able to do both....

here is the output of fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

Device Boot Start End Blocks Id System
/dev/sda1 10 1315 10485760 7 HPFS/NTFS
/dev/sda2 * 1315 9147 62914560 7 HPFS/NTFS
/dev/sda3 9148 19458 82815716 f W95 Ext'd (LBA)
/dev/sda4 * 19131 19458 2620416 c W95 FAT32 (LBA)
/dev/sda5 9148 9755 4883728+ 83 Linux
/dev/sda6 9756 19130 75302912 7 HPFS/NTFS
/dev/sda7 19131 19458 2620416 dd Unknown

and output of df -h: (presently on live cd)

Filesystem Size Used Avail Use% Mounted on
tmpfs 1009M 16M 994M 2% /lib/modules/2.6.24-16-generic/volatile
tmpfs 1009M 16M 994M 2% /lib/modules/2.6.24-16-generic/volatile
varrun 1009M 104K 1009M 1% /var/run
varlock 1009M 0 1009M 0% /var/lock
udev 1009M 80K 1009M 1% /dev
devshm 1009M 12K 1009M 1% /dev/shm
tmpfs 1009M 36K 1009M 1% /tmp
df: `/home/ubuntu/.gvfs': Transport endpoint is not connected
/dev/sda4 2.5G 633M 1.9G 25% /media/MEDIADIRECT
/dev/sda6 72G 60G 13G 84% /media/New Volume
/dev/sda1 10G 5.2G 4.9G 52% /media/RECOVERY
/dev/sda2 60G 56G 4.6G 93% /media/OS
/dev/sda5 4.6G 4.1G 259M 95% /media/disk



When I tried loading gparted, it is not listing the different partitions...instead, it is listing the entire HDD as a single partition...

So I am not able to make any changes....

please help me out ....thanks

---

### Post by overdrank on 2009-08-13
Please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by Post Monkeh on 2009-08-13
are you running install until you get to the partition section, or are you selecting "try ubuntu without making any changes to the computer" and loading gparted from "system>admin>partition editor"

---

### Post by madhavhmk on 2009-08-13
I am using the second option...

I booted from lice cd, and clicked the partition editor...

but here, the HDD is being listed as a single 160 GB (unallocated) partition...

---

