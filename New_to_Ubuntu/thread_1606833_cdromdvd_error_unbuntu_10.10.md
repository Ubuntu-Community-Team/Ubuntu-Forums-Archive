---
title: "cdrom/dvd error unbuntu 10.10"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by fraggleos on 2010-10-27
I am having trouble with dvd-rom mounting here is fstab - 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2fac943d-eb19-4c25-99a6-d6b8ac75013b none            swap    sw              0       0

---

