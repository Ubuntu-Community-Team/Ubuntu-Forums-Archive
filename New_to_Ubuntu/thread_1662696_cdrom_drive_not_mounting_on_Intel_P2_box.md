---
title: "cdrom drive not mounting on Intel P2 box"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by Cafargo on 2011-01-08
Greetings All.

Curiously, I noticed today that my only cdrom device is not mounting. It's as if it doesn't even exist. Here is the entry in my fstab:

[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ea54f20e-02b7-4360-bbf7-d9fc9c32224c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a40493ae-462a-426c-a413-d4c842f42e50 none            swap    sw              0       0
# /dev/sdb1
UUID=30cdf37b-1659-40d3-a607-9717673a3ccf /Disk_2         ext2
/dev/scd0       /media/cdrom0    udf,iso9660 user,noauto,exec,utf8 0       0[/HTML]

But, xubuntu 9.04 can't find the device either when I want to burn data or try to load a CD. The bios entry looks very normal. Outside appearance looks fine, the green light flashes and stuff.

Would anyone have some troubleshooting tips or posts you can direct me to.

Many thanks!
Cheers,
Pierre.

---

