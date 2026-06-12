---
title: "/dev/fd0  Does Not Exist error message"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-03-28
Cannot mount floppy drive.

eld@House:/$ ls /media
cdrom  cdrom0  cdrom1  floppy0

eld@House:/$ sudo mount  -t vfat  /dev/fd0  /media/floppy0
mount: special device /dev/fd0 does not exist
eld@House:/$ 



fstab file:

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

# Floppy Drive
/dev/fd0        /media/floppy0     auto   rw,user,noauto,exec,utf8    0  0

*******************************

I am stumped. Any ideas anybody?
I have things where there supposed to be according to my Linux book and what ya'll have suggested.

---

### Post by kanikilu on 2009-03-28
Check to see that the floppy module is loaded with ```
lsmod | grep floppy
``` If it's not, use ```
sudo modprobe floppy
``` to load it. Add **floppy** to /etc/modules if you want it loaded automatically from now on.

---

### Post by ozark_hillbilly on 2009-03-28
Thanks!

modprobe command seemed to do the trick!

---

### Post by kanikilu on 2009-03-28
No problem. Just add floppy to your /etc/modules file so you don't have to do that every time :)

---

