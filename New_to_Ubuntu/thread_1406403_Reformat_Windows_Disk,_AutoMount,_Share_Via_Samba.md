---
title: "Reformat Windows Disk, AutoMount, Share Via Samba"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by rockinthesixstring on 2010-02-13
Hi All
I'm new to the Linux world, but I'm seeing huge possibilities.  I'm currently working on a project and can't get past step ONE.

1) Mount Disk 
2) Share with Samba

I have a 1.5TB disk that I'm trying to mount.
```
sudo fdisk -l
``````
Disk /dev/sda: 64.1 GB, 64105742336 bytes
255 heads, 63 sectors/track, 7793 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97f997f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7469    59994711   83  Linux
/dev/sda2            7470        7793     2602530    5  Extended
/dev/sda5            7470        7793     2602498+  82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78c5ebd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS

```/dev/sdb1 is the one I'm trying to mount.

My fstab looks like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e117bab1-d0ea-4833-b11a-0e65c137a7b2 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=7275d130-8db1-4a8d-a771-55a996e81824 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1     /media/media ntfs-3g defaults,locale=en_US.utf8   0    0
```Any yes I did "mkdir /media/media"

When I try to run this command
```
sudo mount -a
```I get the following output

```
Failed to write lock '/dev/sdb1': Resource temporarily unavailable
Error opening '/dev/sdb1': Resource temporarily unavailable
Failed to mount '/dev/sdb1': Resource temporarily unavailable
```NOTE: There's a good chance that there's a problem with the disk since I've been messing around so much.

My ultimate goal is to have a stable file share so that I can dump my media files onto the disk from my home network (consisting of Mac's PC's and now Linux)

Any help would be greatly appreciated.

---

### Post by rockinthesixstring on 2010-02-14
bump from page 7

---

### Post by rockinthesixstring on 2010-02-14
I changed and formatted the file system, but I still can't get it to mount
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   83  Linux

```

---

### Post by rockinthesixstring on 2010-02-14
OK, looks like my fstab is right now.  Now I can mount the disk.
```
sudo nano /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e117bab1-d0ea-4833-b11a-0e65c137a7b2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7275d130-8db1-4a8d-a771-55a996e81824 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1     /media/media               ext2               defaults     0             0

```

---

