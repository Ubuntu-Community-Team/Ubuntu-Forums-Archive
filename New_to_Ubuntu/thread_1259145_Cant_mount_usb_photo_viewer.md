---
title: "Cant mount usb photo viewer"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by nakama85 on 2009-09-06
I have a "Coby Cliphanger" Pocket size photo viewer.
When I plug it in the usb drive shows up, but when I double click it I get the "Cannot mount file" err.

Any thoughts?

Thanks

---

### Post by hal10000 on 2009-09-06
With the photo viewer plugged in, post the outputs of the commands [COLOR="Red"]lsusb[/COLOR] and [COLOR="Red"]sudo fdisk -l[/COLOR]

---

### Post by nakama85 on 2009-09-06
thanks for the responce.

"Lsusb"
```
Bus 005 Device 008: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
Bus 005 Device 007: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 1403:0001 [COLOR="green"]Sitronix Digital Photo Frame[/COLOR]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1532:0109 Razer USA, Ltd 
Bus 001 Device 006: ID 046d:c043 Logitech, Inc. MX320 Laser Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

"sudo fdisk -l"

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe397e397

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2           60291       60801     4104607+  82  Linux swap / Solaris
/dev/sda3            2433       60290   464744385   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57d557d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdg: 2 MB, 2097152 bytes
1 heads, 4 sectors/track, 1024 cylinders
Units = cylinders of 4 * 512 = 2048 bytes
Disk identifier: 0xa06fa207

Disk /dev/sdg doesn't contain a valid partition table

```

---

### Post by hal10000 on 2009-09-06
> Disk /dev/sdg doesn't contain a valid partition table
This seems to be the photo viewer.
But there's no partition table. Is it empty, or can you see any files if you use it under e.g. windows?
If it contains no data, then you first have to create a partition on the device, i would suggest to create a fat32 partition, so you can use it under windows and linux.
you can do that with a partition manager, e.g. gparted, but be careful because you will destroy any existing data on the device.


EDIT: I found this, maybe it's importan for you: [http://www.nabble.com/Photo-keyring-compatible-with-standards--td21567218.html](http://www.nabble.com/Photo-keyring-compatible-with-standards--td21567218.html)

---

