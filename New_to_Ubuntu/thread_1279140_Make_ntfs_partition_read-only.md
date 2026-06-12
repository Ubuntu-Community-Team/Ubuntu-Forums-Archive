---
title: "Make ntfs partition read-only"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by AlphaLexman on 2009-09-30
I want to make my ntfs partition read-only when I click its icon in nautilus.
When the drive is not mounted, clicking on the icon asks me for my password and gives me read-_write_ permissions.  Only occasionally do I need to write.  I am trying to get it so that I don't have to enter a password for read-only.

Some web searching indicates I need an entry in fstab.
Here is my /etc/fstab: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a4993c1d-7079-471f-8fd3-30f73e4a3cbd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=accd6416-2173-4066-bd6a-84a4a277af9c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```/dev/sdb1 is ubuntu, mounted at /
/dev/sda1 is WinXP, mounted at/media/Sata_Disk_0
/dev/sdc1 is Fat32, mounted at /media/THERMALTAKE

Another thing, why does my cd-rw drive (cdrom1) not show in fstab?

---

### Post by AlphaLexman on 2009-09-30
Found a good post [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

I can probably fix this myself

---

