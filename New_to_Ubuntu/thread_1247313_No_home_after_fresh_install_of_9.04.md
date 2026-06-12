---
title: "No /home after fresh install of 9.04"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by jerrynewt on 2009-08-22
Just reinstalled 9.04 on my daughters comp. (Toshiba Satellite Pro 6100-120 Gig hd-763 Megs ram) Before install I had 40 gigs to / (sda22) and 80 gigs for /home (sda3). After install of system on sda2 (leaving sda3 completely alone) sda3 now shows up as /media/disk, with no previous settings enabled such as themes fonts and wallpapers or Firefox addons. The information is still all there as I can mount the /media/disk partition and see everything just fine. Any way I can fix this without destroying my old home settings? Thanks for the help and time.

---

### Post by PukingPenguin on 2009-08-22
There are a couple of ways to handle this, all fairly easy. It might be best if you could post the output of ```
cat /etc/fstab
```

and some genius will be able to tell you how to edit it to make /media/disk become /home.

The other possibility is to symlink your existing /home to /media/disk.

---

### Post by jerrynewt on 2009-08-22
Here are the results of cat /etc/fstab


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=95ff0ed1-76df-46ec-a41e-59371532efb5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5878b5a-f3f6-46c7-9240-ec00299285e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by jerrynewt on 2009-08-22
Bump??

---

### Post by ks07 on 2009-08-22
Could you please show the output of
```
sudo fdisk -l
```?

---

### Post by jerrynewt on 2009-08-22
Output of sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421   83  Linux
/dev/sda2           14312       14593     2265165    5  Extended
/dev/sda3            5738       14311    68870655   83  Linux
/dev/sda5           14312       14593     2265133+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by ks07 on 2009-08-22
I was just about to write up a little explanation for you, but I just found exactly what you're looking for. [See this post.]("http://ubuntuforums.org/showpost.php?p=6964687&postcount=6")

---

