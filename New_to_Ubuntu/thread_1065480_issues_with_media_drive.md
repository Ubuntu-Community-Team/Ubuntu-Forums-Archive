---
title: "issues with media drive"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by zetagirl on 2009-02-09
here is my fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=489be023-9ba0-4dac-81ff-cb717e6e656f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=50fb6460-8719-4e47-8295-c5877fe678bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb5      /media/HP ntfs-3g defaults,force 0 0
/dev/sdb1     /media/MMCSD     auto     user,auto,exec,rw     0     0

i cant figure out y its not finding my media drive...when I click on the media drive it says 'You are not privileged to mount the volume 'HP Personal Media Drive'.

---

### Post by Nepherte on 2009-02-10
Try to add the user or users option for the media drive.

---

### Post by zetagirl on 2009-02-10
how would i do that?

---

