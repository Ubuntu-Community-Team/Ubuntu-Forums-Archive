---
title: "How to auto mount FAT32 partition at start up"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by leonardo_neo on 2009-04-06
Hello everyone,

I have done a fresh install of Ubuntu 9.04. (dual boot with Xp)

**I want to auto mount my FAT32 common partition at startup, with _read & write support intact_.**

This is my sudo fdisk -l output 

> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1785    14337981    7  HPFS/NTFS
/dev/sda2            2978        4864    15157327+   b  W95 FAT32
/dev/sda3            1786        2636     6835657+  83  Linux
/dev/sda4            2637        2977     2739082+   5  Extended
/dev/sda5            2637        2977     2739051   82  Linux swap / Solaris

Partition table entries are not in disk order


I have also checked my FAT32 partition with gparted, and it is sda2

This is my /etc/fstab output...

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=3ed3878f-8103-45f2-b9d4-bb2aa1dbbb00 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7bf9d711-4de5-477f-9406-c3de6482b70c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Now let me tell you what I have already tried.....

I have tried to create a directory in /media named 'common' and tried these two lines_ one at a time....._

> /dev/sda2 /media/common vfat defaults,force 0 0

> /dev/sda2 /media/common vfat unmask=0000  0 0

Unfortunately both of these lines didn't work. After these lines, I can't even mount my FAT32 partition by clicking on that, and I get this message.

>  wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any idea what could be the problem, and what else I can do to resolve this issue??

Thanks in anticipation... :)

---

### Post by Skol312000 on 2009-04-06
the live cd u used must of been "corruoted" or had some error in it..

try burning a different cd...and try again running gparted.


u could also try burning a Gparted live CD and just use taht to fix partitions...

---

### Post by madverb on 2009-04-06
```
sudo mkdir /media/temp
sudo mount -t vfat /dev/sda2 /media/temp
```

Does that work?

---

### Post by leonardo_neo on 2009-04-06
> **madverb said:**
> ```
sudo mkdir /media/temp
sudo mount -t vfat /dev/sda2 /media/temp
```

Does that work?

Yes, this command does mount the volume....but I can't edit the files in this mounted partition now. Also, I can't unmount it by right clicking and selecting 'unmount volume'. It says "Can not unmount volume. The volume common must have been mounted manually in the command line."

So what should be the next step? :)

---

### Post by madverb on 2009-04-06
Cool, just making sure that it could mount.
```
/dev/sda2 /media/common vfat defaults 0 0
```
also make sure that the folder /media/common is created.
```

sudo mkdir /media/common
```

---

### Post by balloooza on 2009-04-06
Ubuntu file manager (naitilus) has a graphical way of doing this, but first

```
sudo umount /dev/sda2
```

to unmount the partition

then erase the lines you have added to the /etc/fstab (and in the future, make sure to make a backup, before you make changes)

then double click the icon on the desktop to mount the disk

then RIGHT click the ICON on the DESKTOP of the disk, and select properties, and tell me when you are there.

---

### Post by leonardo_neo on 2009-04-06
> **balloooza said:**
> Ubuntu file manager (naitilus) has a graphical way of doing this, but first

```
sudo umount /dev/sda2
```

to unmount the partition

then erase the lines you have added to the /etc/fstab (and in the future, make sure to make a backup, before you make changes)

then double click the icon on the desktop to mount the disk

then RIGHT click the ICON on the DESKTOP of the disk, and select properties, and tell me when you are there.

I made the backup of fstab before I started doing this editing...the fstab which I posted in my question is from my back up file only :)

OK, so I unmounted the FAT32 partition, with the command which you gave.

I also created the directory  /media/common

Then I double clicked and mounted the FAT32 partition. What is next?

Am I supposed to do this, or should I first add the line [HTML]/dev/sda2 /media/common vfat defaults 0 0[/HTML] in fstab, and then try to mount?? :)

---

### Post by balloooza on 2009-04-06
First try to see if you can modify files, and if you can go in the properties window for the drive (right click on the desktop icon) and see if you have a voloume tab (I am running 8.04 now, some things change from version to version, it might be somthing different)

---

### Post by madverb on 2009-04-06
Nevermind that... the reason it wasn't automounting on boot was because you hadn't created the /media/common directory. It will now mount on boot with that fstab entry.

---

### Post by leonardo_neo on 2009-04-06
> **balloooza said:**
> First try to see if you can modify files, and if you can go in the properties window for the drive (right click on the desktop icon) and see if you have a voloume tab (I am running 8.04 now, some things change from version to version, it might be somthing different)

OK, so now my fstab entry is again as it was in default setting. Now I mount the common FAT32 partition with double click, and it is mounted. I can also modify files in this mounted partition.Now I right click and this is what I see in volume.


@madverb
It did mount when I made the 'temp' directory and entered the next command. But when I make the 'common' directory, and enter the line which you gave in the fstab, it refuses to mount the volume.

---

### Post by madverb on 2009-04-06
have you restarted your computer after doing all that?

---

### Post by leonardo_neo on 2009-04-06
> **madverb said:**
> have you restarted your computer after doing all that?

Nope....let me try that then. :)

---

### Post by leonardo_neo on 2009-04-06
> **madverb said:**
> have you restarted your computer after doing all that?

OK, so now it **does** auto mount the volume at startup...But now I can't edit files in this volume. I can only read. I can't create any files.

And this is what I see in volume tab now *after * I changed the fstab...

:)

---

### Post by leonardo_neo on 2009-04-07
I have resolved the issue.

In fstab the line > /dev/sda2 /media/common vfat umask=0000 0 0  finally resolved the issue.

Before I was typing 'umask' as 'unmask' and that was the reason the partition was not able to mount.

Now I can 'edit' files in this FAT32 partition, and also it is auto mounted at startup. But I can't unmount it with right click and selecting 'unmount volume'. Anyway, I am happy that the problem is solved.

Thanks to *madverb* and *balloooza* for your sincere efforts :)

---

