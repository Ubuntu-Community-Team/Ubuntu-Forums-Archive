---
title: "HDD not showing up in places"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by davidooms on 2009-04-24
Hi, complete Ubunto noob here ... finally decided to make the switch from Windows and after 3 days decided to format my internal 500 GB data drive to ext3. Problem is the drive is no longer showing up in 'places' now, although I can find it in fdisk. Geparted also shows disk.

fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4225e0e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         719     5767168    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             719       26471   206852092    7  HPFS/NTFS
/dev/sda3           26472       30401    31567725    5  Extended
/dev/sda5           26472       30233    30218233+  83  Linux
/dev/sda6           30234       30401     1349428+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca1deb28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a12e5b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4225e0e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         719     5767168    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             719       26471   206852092    7  HPFS/NTFS
/dev/sda3           26472       30401    31567725    5  Extended
/dev/sda5           26472       30233    30218233+  83  Linux
/dev/sda6           30234       30401     1349428+  82  Linux swap / Solaris

[COLOR=Red]Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca1deb28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux[/COLOR]

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a12e5b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS

Can anybody help?

---

### Post by teamkiller87 on 2009-04-24
Is that hard drive mounted? Try "sudo mount" followed by the path to your HDD.

---

### Post by crjackson on 2009-04-24
> **davidooms said:**
> Hi, complete Ubunto noob here ... finally decided to make the switch from Windows and after 3 days decided to format my internal 500 GB data drive to ext3. Problem is the drive is no longer showing up in 'places' now, although I can find it in fdisk. Geparted also shows disk.

fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4225e0e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         719     5767168    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             719       26471   206852092    7  HPFS/NTFS
/dev/sda3           26472       30401    31567725    5  Extended
/dev/sda5           26472       30233    30218233+  83  Linux
/dev/sda6           30234       30401     1349428+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca1deb28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a12e5b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4225e0e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         719     5767168    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             719       26471   206852092    7  HPFS/NTFS
/dev/sda3           26472       30401    31567725    5  Extended
/dev/sda5           26472       30233    30218233+  83  Linux
/dev/sda6           30234       30401     1349428+  82  Linux swap / Solaris

[COLOR=Red]Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca1deb28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux[/COLOR]

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a12e5b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS

Can anybody help?

It looks like you installed Ubuntu to that drive. If this is the case it shows up as "File System" rather than a drive lable.

---

