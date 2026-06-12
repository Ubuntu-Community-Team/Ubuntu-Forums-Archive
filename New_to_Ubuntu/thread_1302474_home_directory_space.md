---
title: "home directory space"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by froglegs on 2009-10-27
I have freshly installed mythbuntu 9.04 with automatic partitioning.  I am trying to move backed up files to my home directory but I do not have access to space available.  File Manager gives total free space as 8.7GB.  How can I access the free space?

cat/etc/fstab gives:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c26241a1-5711-4b3d-9f7b-a102330c43cf /               ext3    errors=remount-ro 0       1
# /var/lib was on /dev/sda6 during installation
UUID=147ae4e5-e45b-4ea1-9f82-996d659c24c7 /var/lib        xfs     defaults        0       2
# swap was on /dev/sda5 during installation
UUID=e5aca214-05b8-4471-830b-deef53de9773 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

df -h gives:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  1.7G  8.8G  17% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  324K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  164K  1.5G   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6             454G  245M  454G   1% /var/lib

sudo fdisk -l gives:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ba0b521

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460       60801   476664615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584       60801   475668553+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb761c745

Thanks in advance, Keven

---

