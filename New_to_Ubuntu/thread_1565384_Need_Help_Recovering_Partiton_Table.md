---
title: "Need Help Recovering Partiton Table"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by opticyclic on 2010-08-31
I've messed up my partition table  [again]("http://ubuntuforums.org/showthread.php?t=1032234")!

I think it was when I deleted what appeared to be a Swap partition when I was using the Mandriva LiveCD.
GParted doesn't show the individual partitions anymore.

As far as I can remember, what I am expecting the table to look like is:
50 GB Windows (Primary NTFS - boot)
50 GB Documents (Primary NTFS)
50 GB Extended
- 37 GB Data (Logical - ext4)
- 5 GB LinuxMint (Logical - ext4)
- 6 GB Ubuntu (Logical - ext4)
- 2 GB (Logical - Linux-Swap)

I'm quite concerned with this:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Unable to seek on /dev/sda

```
```

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=104856192, Id= 7, bootable
/dev/sda2 : start=104856255, size=104856255, Id= 7
/dev/sda3 : start=209712699, size=102864006, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=308383803, size=  4192902, Id=82
/dev/sda6 : start=209712699, size= 75601701, Id=83
/dev/sda7 : start=285315072, size= 10489773, Id=83
/dev/sda8 : start=295804928, size= 11927552, Id=83

```
```
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   6526    6527-  52428096    7  HPFS/NTFS
/dev/sda2       6527   13053    6527   52428127+   7  HPFS/NTFS
/dev/sda3      13054+  19456    6403-  51432003    5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      19196+  19456     261-   2096451   82  Linux swap / Solaris
/dev/sda6      13054+  17759    4706-  37800850+  83  Linux
/dev/sda7      17760+  18412     653-   5244886+  83  Linux
/dev/sda8      18413+  19155-    743-   5963776   83  Linux

```
Can someone shed some light for me please.

---

### Post by srs5694 on 2010-08-31
Your sfdisk output looks reasonable, except that your extended partition and the first logical partition (by disk location; /dev/sda6) both begin at exactly the same sector. This isn't normally permitted, since each logical partition must have one associated sector *outside* of the partition itself, but *inside* the extended partition, to define the logical sector's start and end points (among other things). If this is the cause of fdisk's error, you can correct it by using sfdisk to edit the start point and size of the extended partition; just start it one sector earlier and make it one sector longer. [This page of mine](http://www.rodsbooks.com/missing-parts/index.html) describes how in more detail. That said, I haven't checked the start and end points of every partition; it could be there's another error lurking in there that I haven't noticed.

Also, the "unable to seek" error from fdisk is troubling. It could be that it's trying to interpret some bogus data that's making it try to seek past the end of the disk. Another possibility is that you're looking at a hardware fault. You might want to look at the disk's SMART status using a tool such as smartctl. My suspicion is that it's all OK, but it couldn't hurt to look.

---

### Post by opticyclic on 2010-09-01
Thanks for that it was a very useful page.
Unfortunately I chickened out of making the changes from the command line and when I read that TestDisk could sort it out for me!
Parted Magic is a fantastic LiveCD to have around!

---

