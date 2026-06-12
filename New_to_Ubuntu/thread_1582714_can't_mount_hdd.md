---
title: "can't mount hdd"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by krollenhagen on 2010-09-26
I have recently installed Ubuntu on my windows machine.  I have a total of 5 hdds in my pc.

/dev/sda1 is my windows boot drive/partition
/dev/sdb1 is my windows "My Documents" folder
/dev/sdc1 is my media library
/dev/sdd1 is my backup drive
/dev/sde is my ubuntu install drive

I am not able to mount /dev/sdc1 in ubuntu.  It does not show up in Places.

Here is a listing for fdisk -l

[I]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09d109d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6414    51520423+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe692b13e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda880764

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d6a99

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60050   482347008   83  Linux
/dev/sde2           60050       60802     6037505    5  Extended
/dev/sde5           60050       60802     6037504   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x175edc87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      969018   488385040+   7  HPFS/NTFS[/I]

Here is the error that I get when trying to mount the drive with

sudo mount /dev/sdc1 /media/library

is

mount: /dev/sdc1 is not a block device

Any help would be appreciated.

thank you,

Keith

---

### Post by RetchingRabbit on 2010-09-26
Might help to post yer fstab....

---

### Post by CharlesA on 2010-09-26
Try this:

```
sudo mount /dev/sdc1 -t ntfs /media/library
```

---

### Post by bsalem on 2010-09-27
Have a look at the output from 'mount' with no options to see how the Linux thinks the filesystem is mounted, if at all.

The /etc/fstab will tell you how the system tries to mount filesystems at boot, only. It is possible to manually mount a filesystem after boot that will not be in that file. The 'mount' again, no arguments, will give you a snap shot of what the system thinks the filesystems are. The 'df' command will show you the partitions, mount-points and sizes. Be sure
the mount points e.g. /media/somedisk are what you expect.

If the filesystem just won't mount, It could be corrupt. You should look at it with Windows and make sure it is OK and do whatever you need to do from Windows to make it OK. Then it should mount from Linux.  I am using an NTFS from Ubuntu 8.10 and there are situations when corruption causes the filesystem to go read-only. I need to at least boot in Windows (Vista) to bring it back for Linux. In all honesty I do not know for sure that the NTFS driver works better in one of the later releases, it may.

---

### Post by krollenhagen on 2010-09-27
> **RetchingRabbit said:**
> Might help to post yer fstab....

Here is my fstab listing

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde1 during installation
UUID=0da8aa79-94c0-48e3-aab1-34aadc373023 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=63c98efd-aab2-45cb-a798-fd7da6110079 none            swap    sw              0       0

---

### Post by krollenhagen on 2010-09-27
> **CharlesA said:**
> Try this:

```
sudo mount /dev/sdc1 -t ntfs /media/library
```

I tried this and here is the response.

```
keith@ubuntu10:~$ sudo mount /dev/sdc1 -t ntfs /media/storage
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory

ntfs-3g 2010.3.6 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
```

---

### Post by CharlesA on 2010-09-27
Hrm, that should have worked.

Can you post the fdisk -l again?

---

### Post by krollenhagen on 2010-09-27
> **CharlesA said:**
> Hrm, that should have worked.

Can you post the fdisk -l again?

Here is my fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde1 during installation
UUID=0da8aa79-94c0-48e3-aab1-34aadc373023 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=63c98efd-aab2-45cb-a798-fd7da6110079 none            swap    sw              0       0
```

I booted to winxp and did a chkdsk on the drive that won't mount.  there were some errors on it.  chkdsk seemed to fix those errors.  now, when I try to mount it, I get the following.

```
keith@ubuntu10:~$ sudo mount /dev/sdc1 /media/storage
mount: special device /dev/sdc1 does not exist

```

and here is my fdisk -l listing
```
keith@ubuntu10:~$ sudo fdisk -l
[sudo] password for keith: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09d109d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6414    51520423+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe692b13e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda880764

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x175edc87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d6a99

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60050   482347008   83  Linux
/dev/sde2           60050       60802     6037505    5  Extended
/dev/sde5           60050       60802     6037504   82  Linux swap / Solaris
keith@ubuntu10:~$ mount /dev/sdc1 /media/storage
mount: only root can do that
keith@ubuntu10:~$ sudo mount /dev/sdc1 /media/storage
mount: special device /dev/sdc1 does not exist
keith@ubuntu10:~$ gedit /etc/fstab
keith@ubuntu10:~$ sudo mount /dev/sdc1 /media/storage
mount: special device /dev/sdc1 does not exist
keith@ubuntu10:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09d109d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6414    51520423+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe692b13e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda880764

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x175edc87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d6a99

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60050   482347008   83  Linux
/dev/sde2           60050       60802     6037505    5  Extended
/dev/sde5           60050       60802     6037504   82  Linux swap / Solaris

```

Any ideas?  The hd does not show up in Places either.  I don't know if I mentioned that before or not.

Thank you,

Keith

---

### Post by CharlesA on 2010-09-27
I don't know why it's not mounting. Did chkdsk fix all the errors on it?

---

### Post by krollenhagen on 2010-09-27
Yes, chkdsk fixed all the errors.

---

### Post by CharlesA on 2010-09-27
> **krollenhagen said:**
> Yes, chkdsk fixed all the errors.

Ok, try this:

Boot off a Livecd and see if that drive is listed in the places menu.

---

### Post by krollenhagen on 2010-09-28
I can't find my Ubuntu cd, but I boot'd with my SystemRescueCD disc and I could mount it with that, without any issues.

Keith

---

