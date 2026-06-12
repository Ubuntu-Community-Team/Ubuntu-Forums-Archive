---
title: "LVM problem: plz help me recover my data"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by ElFerry on 2011-02-13
For so far I lost 2,4 TB of data. I hope there is some one how can help my recover my data. 

Recently I installed Ubuntu 10.10. using LVM. I made two Volume Groups; system and data. VG data consists out three Logical Volumes; data, data-backup and data_downloads. data and data_backup are both raid arrays. LV data uses a 2,4 TB raid0 array and data_backup a 250 GB raid1 array:

[HTML]grandmasterf@action-server:~$ sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid0 sda7[0] sdb7[1]
      2344336256 blocks 64k chunks
      
md0 : active raid1 sda6[0] sdb6[1]
      244139968 blocks [2/2] [UU][/HTML]

When i boot my system I get the following messages in the message log:

[HTML]Feb 13 14:11:47 action-server kernel: [    2.612392] md: raid6 personality registered for level 6
Feb 13 14:11:47 action-server kernel: [    2.612400] md: raid5 personality registered for level 5
Feb 13 14:11:47 action-server kernel: [    2.612406] md: raid4 personality registered for level 4
Feb 13 14:11:47 action-server kernel: [    2.628800] md: raid10 personality registered for level 10
Feb 13 14:11:47 action-server kernel: [    2.663768] md: bind<sdb6>
Feb 13 14:11:47 action-server kernel: [    2.670219] md: bind<sdb7>
Feb 13 14:11:47 action-server kernel: [    2.741730] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.3/usb5/5-2/5-2:1.0/input/input5
Feb 13 14:11:47 action-server kernel: [    2.742022] generic-usb 0003:046D:C01D.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.3-2/input0
Feb 13 14:11:47 action-server kernel: [    2.776071] md: bind<sda7>
Feb 13 14:11:47 action-server kernel: [    2.777861] md: bind<sda6>
Feb 13 14:11:47 action-server kernel: [    2.781830] md/raid1:md0: active with 2 out of 2 mirrors
Feb 13 14:11:47 action-server kernel: [    2.781876] md0: detected capacity change from 0 to 249999327232
Feb 13 14:11:47 action-server kernel: [    2.785201]  md0:
Feb 13 14:11:47 action-server kernel: [    2.788466] md/raid0:md1: looking at sda7
Feb 13 14:11:47 action-server kernel: [    2.788474] md/raid0:md1:   comparing sda7(2344337280) with sda7(2344337280)
Feb 13 14:11:47 action-server kernel: [    2.788482] md/raid0:md1:   END
Feb 13 14:11:47 action-server kernel: [    2.788487] md/raid0:md1:   ==> UNIQUE
Feb 13 14:11:47 action-server kernel: [    2.788492] md/raid0:md1: 1 zones
Feb 13 14:11:47 action-server kernel: [    2.788497] md/raid0:md1: looking at sdb7
Feb 13 14:11:47 action-server kernel: [    2.788502] md/raid0:md1:   comparing sdb7(2344335232) with sda7(2344337280)
Feb 13 14:11:47 action-server kernel: [    2.788510] md/raid0:md1:   NOT EQUAL
Feb 13 14:11:47 action-server kernel: [    2.788515] md/raid0:md1:   comparing sdb7(2344335232) with sdb7(2344335232)
Feb 13 14:11:47 action-server kernel: [    2.788520] md/raid0:md1:   END
Feb 13 14:11:47 action-server kernel: [    2.788525] md/raid0:md1:   ==> UNIQUE
Feb 13 14:11:47 action-server kernel: [    2.788529] md/raid0:md1: 2 zones
Feb 13 14:11:47 action-server kernel: [    2.788535] md/raid0:md1: FINAL 2 zones
Feb 13 14:11:47 action-server kernel: [    2.788543] md/raid0:md1: zone 1
Feb 13 14:11:47 action-server kernel: [    2.788548] md/raid0:md1: checking sda7 ... contained as device 0
Feb 13 14:11:47 action-server kernel: [    2.788555] md/raid0:md1:  (2344337280) is smallest!.
Feb 13 14:11:47 action-server kernel: [    2.788559] md/raid0:md1: checking sdb7 ... nope.
Feb 13 14:11:47 action-server kernel: [    2.788564] md/raid0:md1: zone->nb_dev: 1, sectors: 2048
Feb 13 14:11:47 action-server kernel: [    2.788568] md/raid0:md1: current zone start: 2344337280
Feb 13 14:11:47 action-server kernel: [    2.788572] md/raid0:md1: done.
Feb 13 14:11:47 action-server kernel: [    2.788576] md/raid0:md1: md_size is 4688672512 sectors.
Feb 13 14:11:47 action-server kernel: [    2.788580] ******* md1 configuration *********
Feb 13 14:11:47 action-server kernel: [    2.788584] zone0=[sda7/sdb7/]
Feb 13 14:11:47 action-server kernel: [    2.788592]         zone offset=0kb device offset=0kb size=2344335232kb
Feb 13 14:11:47 action-server kernel: [    2.788597] zone1=[sda7/]
Feb 13 14:11:47 action-server kernel: [    2.788603]         zone offset=2344335232kb device offset=1172167616kb size=1024kb
Feb 13 14:11:47 action-server kernel: [    2.788606] **********************************
Feb 13 14:11:47 action-server kernel: [    2.788608] 
Feb 13 14:11:47 action-server kernel: [    2.788625] md1: detected capacity change from 0 to 2400600326144
Feb 13 14:11:47 action-server kernel: [    2.792610]  md1: p1 < unknown partition table
Feb 13 14:11:47 action-server kernel: [    2.809170]  >
.
.
.
Feb 13 14:11:47 action-server kernel: [    3.153393] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 14:11:47 action-server kernel: [    3.258905] device-mapper: ioctl: error adding target to table
Feb 13 14:11:47 action-server kernel: [    3.293292] device-mapper: ioctl: error adding target to table
Feb 13 14:11:47 action-server kernel: [    4.292936] Adding 1949692k swap on /dev/mapper/system-swap.  Priority:-1 extents:1 across:1949692k 
Feb 13 14:11:47 action-server kernel: [    4.429172] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Feb 13 14:11:47 action-server kernel: [    4.573033] EXT4-fs (dm-2): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 14:11:47 action-server kernel: [    4.607734] EXT4-fs (dm-3): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 14:11:47 action-server kernel: [    4.659808] EXT4-fs (dm-4): mounted filesystem with ordered data mode. Opts: (null)
.
.
.
Feb 13 14:11:47 action-server kernel: [    8.687287] EXT4-fs (dm-6): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 14:11:47 action-server kernel: [    9.399448] EXT4-fs (dm-7): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 14:11:47 action-server kernel: [    9.528407] EXT4-fs (dm-8): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 14:11:47 action-server kernel: [    9.717105] EXT4-fs (dm-9): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 14:11:47 action-server kernel: [   22.151307] EXT4-fs (dm-10): mounted filesystem with ordered data mode. Opts: (null)
.
.
.
Feb 13 14:11:56 action-server kernel: [  124.501443] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro,commit=0
Feb 13 14:11:56 action-server kernel: [  124.545595] EXT4-fs (dm-2): re-mounted. Opts: commit=0
Feb 13 14:11:56 action-server kernel: [  124.911586] EXT4-fs (dm-3): re-mounted. Opts: commit=0
Feb 13 14:11:57 action-server kernel: [  125.202952] EXT4-fs (dm-4): re-mounted. Opts: commit=0
Feb 13 14:11:57 action-server kernel: [  125.844936] EXT4-fs (dm-5): re-mounted. Opts: commit=0
Feb 13 14:11:57 action-server kernel: [  125.850701] EXT4-fs (dm-6): re-mounted. Opts: commit=0
Feb 13 14:11:57 action-server kernel: [  125.868362] EXT4-fs (dm-7): re-mounted. Opts: commit=0
Feb 13 14:11:57 action-server kernel: [  125.873612] EXT4-fs (dm-8): re-mounted. Opts: commit=0
Feb 13 14:11:58 action-server kernel: [  126.004948] EXT4-fs (dm-9): re-mounted. Opts: commit=0
Feb 13 14:11:58 action-server kernel: [  126.010569] EXT4-fs (dm-10): re-mounted. Opts: commit=0
Feb 13 14:11:59 action-server kernel: [  127.634280] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro,commit=0
Feb 13 14:11:59 action-server kernel: [  127.737621] EXT4-fs (dm-2): re-mounted. Opts: commit=0
Feb 13 14:11:59 action-server kernel: [  127.969372] EXT4-fs (dm-3): re-mounted. Opts: commit=0
Feb 13 14:12:00 action-server kernel: [  128.111243] EXT4-fs (dm-4): re-mounted. Opts: commit=0
Feb 13 14:12:00 action-server kernel: [  128.781787] EXT4-fs (dm-5): re-mounted. Opts: commit=0
Feb 13 14:12:00 action-server kernel: [  128.787226] EXT4-fs (dm-6): re-mounted. Opts: commit=0
Feb 13 14:12:01 action-server kernel: [  129.292393] EXT4-fs (dm-7): re-mounted. Opts: commit=0
Feb 13 14:12:01 action-server kernel: [  129.298921] EXT4-fs (dm-8): re-mounted. Opts: commit=0
Feb 13 14:12:01 action-server kernel: [  129.937129] EXT4-fs (dm-9): re-mounted. Opts: commit=0
Feb 13 14:12:01 action-server kernel: [  129.956373] EXT4-fs (dm-10): re-mounted. Opts: commit=0[/HTML]

During boot the system asked to skip mounting LV data or to recover it in recovery mode. 

In the following I try the make things clear by giving you the result of some commands from the command line:

PV sacn:

[HTML]grandmasterf@action-server:~$ sudo pvscan
  Couldn't find device with uuid '5ZRC0x-GliU-wP0o-xyTr-SIbd-KdQZ-jHJkZA'.
  PV /dev/sda5        VG system   lvm2 [44.70 GiB / 7.45 GiB free]
  PV /dev/sdb5        VG system   lvm2 [46.56 GiB / 4.67 GiB free]
  PV unknown device   VG data     lvm2 [232.83 GiB / 0    free]
  PV /dev/md1         VG data     lvm2 [2.18 TiB / 0    free]
  Total: 4 [511.82 GiB] / in use: 4 [511.82 GiB] / in no VG: 0 [0   ][/HTML]


VG scan:

[HTML]grandmasterf@action-server:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "system" using metadata type lvm2
  Couldn't find device with uuid '5ZRC0x-GliU-wP0o-xyTr-SIbd-KdQZ-jHJkZA'.
  Found volume group "data" using metadata type lvm2[/HTML]

LV scan:

[HTML]grandmasterf@action-server:~$ sudo lvscan
  ACTIVE            '/dev/system/root' [952.00 MiB] inherit
  ACTIVE            '/dev/system/swap' [1.86 GiB] inherit
  ACTIVE            '/dev/system/home' [9.31 GiB] inherit
  ACTIVE            '/dev/system/tmp' [1.86 GiB] inherit
  ACTIVE            '/dev/system/var' [27.94 GiB] inherit
  ACTIVE            '/dev/system/usr' [14.90 GiB] inherit
  ACTIVE            '/dev/system/usr_local' [7.45 GiB] inherit
  ACTIVE            '/dev/system/opt' [7.45 GiB] inherit
  ACTIVE            '/dev/system/srv' [7.45 GiB] inherit
  Couldn't find device with uuid '5ZRC0x-GliU-wP0o-xyTr-SIbd-KdQZ-jHJkZA'.
  ACTIVE            '/dev/data/data_downloads' [186.26 GiB] inherit
  ACTIVE            '/dev/data/data_backup' [232.83 GiB] inherit
  inactive          '/dev/data/data' [2.00 TiB] inherit[/HTML]

"fdisk -l" command:

[HTML]Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f759

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         244     1951744   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             244      182402  1463184385    5  Extended
/dev/sda5             244        6079    46873600   8e  Linux LVM
/dev/sda6            6079       36473   244140032   fd  Linux raid autodetect
/dev/sda7           36474      182402  1172168704   fd  Linux raid autodetect

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008cde2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182402  1465137153    5  Extended
/dev/sdb5               1        6079    48827392   8e  Linux LVM
/dev/sdb6            6079       36474   244140032   fd  Linux raid autodetect
/dev/sdb7           36474      182402  1172167680   fd  Linux raid autodetect

Disk /dev/md0: 250.0 GB, 249999327232 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b325

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       30394   244137984    5  Extended

Disk /dev/md1: 2400.6 GB, 2400600326144 bytes
2 heads, 4 sectors/track, 586084064 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/dm-0: 998 MB, 998244352 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 1996 MB, 1996488704 bytes
255 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 9999 MB, 9999220736 bytes
255 heads, 63 sectors/track, 1215 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 1996 MB, 1996488704 bytes
255 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table

Disk /dev/dm-4: 30.0 GB, 29997662208 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-4 doesn't contain a valid partition table

Disk /dev/dm-5: 16.0 GB, 15997075456 bytes
255 heads, 63 sectors/track, 1944 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-5 doesn't contain a valid partition table

Disk /dev/dm-6: 7998 MB, 7998537728 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-6 doesn't contain a valid partition table

Disk /dev/dm-7: 7998 MB, 7998537728 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-7 doesn't contain a valid partition table

Disk /dev/dm-8: 7998 MB, 7998537728 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-8 doesn't contain a valid partition table

Disk /dev/dm-9: 200.0 GB, 199996997632 bytes
255 heads, 63 sectors/track, 24314 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/dm-9 doesn't contain a valid partition table

Disk /dev/dm-10: 250.0 GB, 249997295616 bytes
255 heads, 63 sectors/track, 30393 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/dm-10 doesn't contain a valid partition table.[/HTML]

---

### Post by An Sanct on 2011-02-13
After a small research I found, that it would be better to omit my previous post ...

---

### Post by ElFerry on 2011-02-16
After searching the internet for quit a while I found the solution for me.

First I tried:
# sudo vgchange -ay data

This didn't work. I receive a sugestion to add a partial flag...so i did:

# sudo vgchange -ay --partial data

:D:D:DAnd yes there it is...my data is back.

---

### Post by lfhb on 2011-10-15
Stumbled upon this post earlier when trying to recover my own LVM.  The individual steps on this post helped out in case the situation get's more serious as in my case:

[http://www.microdevsys.com/WordPress/2011/09/19/linux-lvm-recovering-a-lost-volume/](http://www.microdevsys.com/WordPress/2011/09/19/linux-lvm-recovering-a-lost-volume/)

Cheers!
L...

---

