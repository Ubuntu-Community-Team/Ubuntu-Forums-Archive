---
title: "unable to mount location"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by stopher87 on 2009-02-17
I know everyone has posted about this, but what's one more. So my windows machine crashed and I am running off a Ubuntu Live cd. I run my system with raid 0 and I finally got that to mount on to Ubuntu and now I can't get my external hard drive to. I did an lsusb so I know it is detected.

> **Bus 002 Device 009: ID 1058:1100 Western Digital Technologies, Inc**. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hu

I can't find the device though when I do an sudo fdisk -l:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000201

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000501

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10511050

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1      182406  1465176163+   7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table


/dev/sde1 is my raid hard drive.

---

### Post by stopher87 on 2009-02-17
bump

---

### Post by stopher87 on 2009-02-17
bump #2

---

### Post by stopher87 on 2009-02-17
bump #3

---

### Post by stopher87 on 2009-02-18
bump #4

---

### Post by stopher87 on 2009-02-18
bump #5

---

### Post by Peter09 on 2009-02-18
My first guess is that you have a failed or corrupt hard drive.

---

