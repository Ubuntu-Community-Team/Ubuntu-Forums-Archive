---
title: "Need to Delete muliple partitions on Dual Boot"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Linuxneophyte on 2009-05-29
[FONT="Times New Roman"][/FONT]I have an HP Pavilion zd8000 which is set up in dual boot mode with XP and Ubuntu. I had installed Ibex first then upgraded to Jackalope. When I couldn't get past the intramfs Busybox, I reinstalled Jaunty from a live CD. Now what you see below is what I have. My file system is so small I can't even download my upgrades.

>  [FONT="Fixedsys"] Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        7574    60830122+   7  HPFS/NTFS
/dev/sda2            7575       12161    36845077+   5  Extended
/dev/sda5            7575       11641    32668146   83  Linux
/dev/sda6           11968       12161     1558273+  82  Linux swap / Solaris
/dev/sda7           11642       11945     2441848+  83  Linux
/dev/sda8           11946       11967      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef8f43c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
roy@roy-laptop:~$ sudo fdisk -l /dev/sda2
[sudo] password for roy: 
roy@roy-laptop:~$ fdisk -l /dev/sda2
Cannot open /dev/sda2
roy@roy-laptop:~$ sudo fdisk -l /dev/sda5

Disk /dev/sda5: 33.4 GB, 33452181504 bytes
255 heads, 63 sectors/track, 4066 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda5 doesn't contain a valid partition table
roy@roy-laptop:~$ sudo fdisk -l /dev/sda6

Disk /dev/sda6: 1595 MB, 1595672064 bytes
255 heads, 63 sectors/track, 193 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda6 doesn't contain a valid partition table
roy@roy-laptop:~$ sudo fdisk -l /dev/sda7

Disk /dev/sda7: 2500 MB, 2500452864 bytes
255 heads, 63 sectors/track, 303 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda7 doesn't contain a valid partition table
roy@roy-laptop:~$ sudo fdisk -l /dev/sda8

Disk /dev/sda8: 180 MB, 180923904 bytes
255 heads, 63 sectors/track, 21 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda8 doesn't contain a valid partition table
[/FONT]


How do I clear out the unnecessary partitions and resize the ones I need to keep?

---

### Post by celticbhoy on 2009-05-29
Gparted.

---

### Post by Tibuda on 2009-05-29
Boot your ubuntu LiveCD and open System > Admin > Partition manager.

---

### Post by Sef on 2009-05-29
> How do I clear out the unnecessary partitions and resize the ones I need to keep?

1) Get [GParted]("http://gparted.sourceforge.net").

2) Get delete all the extended partitions. (sda5 - sda8)

3) Reset the partitions.

---

### Post by lindsay7 on 2009-05-29
Be sure to right click the partition that you want to work on and unmount it first or Gparted will not let you work on it.

---

### Post by ajaysutton on 2009-05-29
Gparted gets my vote.  You can download a bootable CD image from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It's an easy to use tool that should help you delete partitions you don't want and resize the others so they are more usable.

---

