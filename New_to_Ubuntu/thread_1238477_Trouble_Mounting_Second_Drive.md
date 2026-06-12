---
title: "Trouble Mounting Second Drive"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by pcamis on 2009-08-12
Thanks in advance for assistance - figuring out my way through Ubutnu & generally loving it.

I've installed Ubuntu Server on an HP Proliant with two RAID 1 arrays pre-configured.  The installation was completed on the primary array.  I now have a second array that I would like to use for the MySQL databases (I will be running Drupal from this box).  The drives are clean, so reformatting is absolutely an option.

I used "cfdisk" to create an NTFS partition on the secondary array (set to type 07 HPFS/NTFS).  From "fdisk -l" everything looks good (see below).  I then adjusted "fstab" to automatically mount the new NTFS partition to a folder (also see below).  When I try to remount, though, I get an "NTFS signature is missing" error (see final below).

Any thoughts on what I'm doing wrong?  Also, should I even be using NTFS or am I better served with a different format?

Thanks again!


**fdisk results:**
Disk /dev/cciss/c0d0: 36.4 GB, 36414750720 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa81fa81f

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1               1        4396    35310838+  8e  Linux LVM
/dev/cciss/c0d0p2            4397        4427      249007+   5  Extended
/dev/cciss/c0d0p5            4397        4427      248976   83  Linux

Disk /dev/cciss/c0d1: 36.4 GB, 36414750720 bytes
255 heads, 32 sectors/track, 8716 cylinders
Units = cylinders of 8160 * 512 = 4177920 bytes
Disk identifier: 0x00000000

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d1p1               1        8716    35561264    7  HPFS/NTFS


[B]FStab Addition:
[/B]/dev/cciss/c0d1p1       /mnt/drupal     ntfs    nls=utf8,umask=0222 0    0


[B]Mount Error:
[/B]NTFS signature is missing.
Failed to mount '/dev/cciss/c0d1p1': Invalid argument
The device '/dev/cciss/c0d1p1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by zerhacke on 2009-08-12
ntfs mounting on Linux is now usually done with ntfs-3g and there's a handy GTK applet you can find with apt-cache that does all the work for you.

However, you're probably best served making the new disk a etx2 or ext3 filesystem since there's no reason to have ntfs on the disk.  Why force it to work with a hackaround when you can get it native?

---

### Post by pcamis on 2009-08-12
Thanks Zerhacke... I was thinking NTFS in case I wanted to jump in to pull a backup of the database using a Windows server.  Figured if NTFS was just as easy as EXT3 then I'd go that route.

Since sounds like it's not quite as easy, I might as well go the EXT3 route and be done with it.  I know I can always get data from an EXT3 drive within Windows if needed anyway.  Thanks again!

---

