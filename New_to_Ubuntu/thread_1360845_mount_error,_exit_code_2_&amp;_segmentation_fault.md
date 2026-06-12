---
title: "mount error, exit code 2 &amp; segmentation fault"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by StevenPankratz on 2009-12-21
I let my friend borrow my external HDD, which has two NTFS partitions on it.  He copied files from one partition onto his Windows machine, then returned the drive.  Now, when I try to use the HDD, only one filesystem will mount.  The other returns, "Error mounting: mount exited with exit code 2:."  I tried using ntfsfix on the offending drive, but it returns, "  

root@thunder-desktop:~# ntfsfix /dev/sdc2
Mounting volume... Segmentation fault     "

I've tried mounting it manually, but nothing happens when I try - no error messages, but no drive, either!  The other filesystem is no problem; I can umount, remount it into another folder, read files, etc., but the other one is a brick.

My guess is that my friend didn't "safely remove drive" before unplugging the HDD, so the one filesystem he was using is goofed now. How can I "fix" it?  Should I see if it works in a Windows machine, try and fix it there, or is there some way I can do all that through Ubuntu?

This is the fdisk -l output:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       25496   102398310   82  Linux swap / Solaris
/dev/sda3   *       25497       60801   283587412+  83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfcd15f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10444    83891398+   7  HPFS/NTFS
/dev/sdc2           10445      182401  1381244602+   7  HPFS/NTFS

Thanks!  Oh, I'm running Karmic 9.10.16.

---

### Post by StevenPankratz on 2009-12-21
Oh, and these are the contents of fstab, which doesn't seem to see either NTFS file system.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=bc5eb668-cf5e-4557-9d1c-4bb9a36244a9 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=7809fbdc-f407-489d-9554-555e7d2b023a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

