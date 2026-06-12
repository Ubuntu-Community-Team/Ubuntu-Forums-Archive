---
title: "Can't mount drive after reboot - Karmic"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by enzymes on 2009-11-25
Hi,

I'm running MythTV on Ubuntu Karmic after upgrading from Jaunty on a 64bit system.

Karmic has been running well for over a week.

Last night I ran the Update Manager which required a reboot. Now, one of my hard disks won't mount.

I have two identical hard disks - both 1TB. The OS is on one, and the MythTV videos go on the one that won't mount - known as /media/mythmedia

Here's a dump of some useful stuff:

```


myusername@mycomputername:~$ fdisk -l
myusername@mycomputername:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bcb9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      118655   953096256   83  Linux
/dev/sda2          118656      121601    23663745    5  Extended
/dev/sda5          118656      121601    23663713+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0636

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
myusername@mycomputername:~$ sudo mount /media/mythmedia
mount: mount point /media/mythmedia does not exist
myusername@mycomputername:~$ sudo umount /media/mythmedia
umount: /media/mythmedia: not found
myusername@mycomputername:~$ ls /media
cdrom  cdrom0

myusername@mycomputername:/etc$ sudo mount /dev/sdb1
mount: mount point /media/mythmedia does not exist
myusername@mycomputername:/etc$ sudo mount /media/mythmedia
mount: mount point /media/mythmedia does not exist

myusername@mycomputername:/etc$ more fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=619c311b-7a25-4009-b37d-000f3f959281 /               ext3    relatime,error
s=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca77b8b7-e2bc-4ff7-808a-0b62897fb949 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# Second hard drive, mythmedia
/dev/sdb1 /media/mythmedia ext3 defaults 0 1


```

So, I can see that in /media there's no longer a mount point called mythmedia.

I'm guessing (hoping) that the data on that hard drive is still there.

Any suggestions? Why did it fail after the required reboot by Ubuntu?

Thanks in advance! :D


**Update - solved it**

Wouldn't you know it? As soon as I post this, I tried the following:

```

myusername@mycomputername:~$ sudo mkdir /media/mythmedia
myusername@mycomputername:~$ sudo mount /dev/sdb1

```

And all is bliss again! Thanks guys - just posting this question helped me!

---

### Post by the_guv on 2009-11-25
hope this helps ..[URL="http://guvnr.com/pc/mount-partition-permanent"][SIZE=2][COLOR=DeepSkyBlue]
[/COLOR][/SIZE][/URL]**[[SIZE=2][COLOR=DeepSkyBlue]SAVE TIME! Permanent Partition Mount [KARMIC KOALA BIBLE #15][/COLOR][/SIZE]]("http://guvnr.com/pc/mount-partition-permanent")**

---

### Post by ukripper on 2009-11-25
post output of this command:
```
sudo blkid
```

replace /dev/sdb1 by UUID in /etc/fstab you find from blkid. This way your mount will never fail again.

---

