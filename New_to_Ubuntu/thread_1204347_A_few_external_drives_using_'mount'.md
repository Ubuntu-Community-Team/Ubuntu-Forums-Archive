---
title: "A few external drives: using 'mount'"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by m_ad on 2009-07-04
I've read over [this]("http://ubuntuforums.org/showthread.php?t=283131") tutorial quite a bit. I've setup a line in /etc/fstab as follows:

```
LABEL=MyBook	/media/MyBook	ntfs-3g	noauto,user,rw	0	0
```

I'm trying to make the mount command as simple as possible. I issue

```
mount LABEL=MyBook
```

and I get

```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```

I don't want root to mount the drive, because I want me (user matt) to be able to write to the drive. Any input would be appreciated, as well as some advice on how to use /etc/fstab to mount external drives. I have about 8 of them. Again, I would like the 'mount' process to be as simple as possible, as well as write access to me (not only root).


**EDIT:** Also, how do I tell fstab **NOT** to mount certain partitions? Dell shipped my PC with a 'DellUtility' and a 'Recovery' partition that I don't want to see in Places.


**EDIT 2:** I have an old Seagate external connected via USB..

```
ls /dev/disk/by-label -alh
```

gives no sign of it being connected, even if it's mounted. This is a device I want to include in /etc/fstab

---

### Post by m_ad on 2009-07-04
Now an unexpected situation :lolflag:


I tried changing the volume label on my Windows partition using

```
sudo mke2fs -L Windows /dev/sda3
```

Now I can't mount it or boot it. When I try and boot Windows, I get a "Invalid executable format" ???



```
[matt@matt-desktop:~]$ sudo mount /dev/sda3
NTFS signature is missing.
Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

Uh oh, I formatted my Windows partition.....

---

### Post by m_ad on 2009-07-04
Now that I've managed to format both my Windows partition and an external hard drive (that had a lot of data that I hadn't yet backed up - oh well, my fault), I was wondering what type of filesystem to format my external hard drive to? fat or ntfs? Which works better with Ubuntu?

---

### Post by LewRockwell on 2009-07-04
[http://www.partedmagic.com/](http://www.partedmagic.com/)

get it, learn it, enjoy it!

---

### Post by HermanAB on 2009-07-04
FAT or NTFS?

The only time to use FAT is when you use a disk with a device that ONLY understands FAT, for example a camara SD card.  You should never use FAT for anything else, because FAT is unreliable and cannot support large files to name two problems.

NTFS is a very reliable file system, but it is slow and wasteful of disk space.  It is good for use when you need to use a portable disk on both Linux and Windows systems.

Hope that helps!

---

### Post by m_ad on 2009-07-04
Thanks for the responses. So now that I've reformatted my partitions, I'm back to my original question (from the original post).

---

### Post by m_ad on 2009-07-05
Anyone?

---

### Post by m_ad on 2009-07-06
Still can't mount an ntfs partition using the method described in the first post. Bumping this thread.

---

