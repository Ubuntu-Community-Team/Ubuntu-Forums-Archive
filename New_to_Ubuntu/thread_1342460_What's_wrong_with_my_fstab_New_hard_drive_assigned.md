---
title: "What's wrong with my fstab? New hard drive assigned."
date: 2009-11-30
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-11-30
I just installed, ran fdisk, and partitioned a new backup hard drive (sdb1).

It's not showing up as a new hardware device. Does it need a "UUID" ?
If so where do you find this?

Help Please,

Ed

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9360d76a-ddb7-4a4a-8a92-21d35c903ad3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2d31d0c7-73ab-4b92-a354-c34d2bb6bf5c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb1               /media                  ext3    defaults        1 2



# Floppy Drive
/dev/fd0        /media/floppy0     auto     rw,user,noauto,exec,utf8    0  0

**[B][B][B]**[/B][/B][/B]

root@House:/home/ed# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00460046

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       25583   154296292+   5  Extended
/dev/sda5            6375       24610   146480638+  83  Linux
/dev/sda6           24611       25583     7815591   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36de36de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
root@House:/home/ed#

---

### Post by doas777 on 2009-11-30
do you really want to mount sdb to /media? or perhaps a sub? the mount will not succed if the dir does not already exist. 

first create a folder in /media to mount to, then complete the line in the fstab, and reboot

---

### Post by sisco311 on 2009-11-30
Directly using /dev/hd*# or /dev/sd*# is no longer preferred since these device assignments can change between system boots.

Open a terminal and paste:
```
ls -al /dev/disk/by-uuid
```to get the UUID of the partition.

i.e.:```
lrwxrwxrwx 1 root root  10 2009-11-29 17:22 **f36ae9ca-b10d-49d5-8323-f5f7e63dcc69** -> *../../sda2*
```

**f36ae9ca-b10d-49d5-8323-f5f7e63dcc69** is the UUID of my /dev/sda2 partition.

Don't mount the partition directly in /media. Create a new mount point (an empty directory) for it:
```
sudo mkdir /media/**data**
```
replace **data** with the name of the directory where you want to mount the partition.

fstab entry:
```
UUID=*paste-the-UUID-here*    /media/**data**    ext3    relatime    0    2
```

The preferred mount option is now relatime (NOT realtime!!!).

You don't have to reboot,
just ype:
```
sudo mount -a
```to mount the partitions listed in fstab.

---

### Post by ozark_hillbilly on 2009-11-30
Sisco311,

Thank you VERY MUCH!!!!!

It's a "done deal" as they say here in Arkansas.

Ed

---

### Post by sisco311 on 2009-11-30
Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

