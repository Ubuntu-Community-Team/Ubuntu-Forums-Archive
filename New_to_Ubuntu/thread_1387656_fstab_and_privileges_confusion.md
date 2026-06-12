---
title: "fstab and privileges confusion"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by championboxes on 2010-01-22
I'm trying to mount an internal hard drive on a debian machine I have added the line 

```
/dev/hdd1	/media/Storage	ext3	rw,noauto,user,sync	0	0

```

which allows me to mount the drive as a user but not write to it...  I can write to it as root though...

Any help would be appreciated...

here is my fstab file

```
debian:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1	/media/Storage	ext3	rw,noauto,user,sync	0	0

```

and the output of fdisk -l

```
debian:~# fdisk -l

Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         973     7815591   83  Linux
/dev/hda2             974        4982    32202292+   5  Extended
/dev/hda5             974        1338     2931831   82  Linux swap / Solaris
/dev/hda6            1339        4982    29270398+  83  Linux

Disk /dev/hdd: 76.8 GB, 76869918720 bytes
255 heads, 63 sectors/track, 9345 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60456259

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        9345    75063681   83  Linux
debian:~# 

```

---

### Post by nothingspecial on 2010-01-22
Do you own the drive

```
sudo chown -R user:user /media/Storage
```

---

### Post by championboxes on 2010-01-22
> **nothingspecial said:**
> Do you own the drive

```
sudo chown -R user:user /media/Storage
```

That did it thank you

---

### Post by Cheezespread on 2010-01-22
deleted . Already answered.

---

