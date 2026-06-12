---
title: "cdrom won't mount / isn't recognized since installing Karmic"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by klemperal on 2009-12-05
Strange problem here.  When I first installed Karmic, my cdrom drives worked fine.  Then, out of the blue, my cdrom1 started giving me error messages > Unable to mount cdrom1--mount: special device /dev/scd1 does not exist
That drive really isn't very old so I'm thinking it must be something Ubuntu related.  If you have an idea what the problem might be or how I could fix it, please let me know.  I'm pasting my fstab below in case that helps.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9ac3971b-d877-43a1-98dc-9bb0674c0b5a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0f9e62f3-7c36-442d-86e3-44f1e3efee55 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
#none /proc/bus/usb usbfs devgid= 121:alex="color: rgb(51, 51, #255);",devmode=664 0 0

---

### Post by Shazaam on 2009-12-05
I have two drives; a cd-rw/dvd-rom and a dvd/rw. This is my fstab...
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=3b0453ab-a2ad-420f-88ad-7d79a722cc47 /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
Both are PATA not SATA. You might try commenting out scd1. Reboot and see what happens.

---

