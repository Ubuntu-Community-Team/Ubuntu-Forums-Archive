---
title: "Fstab problem"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-07-29
Fstab:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=a3b754c2-c72c-4200-bb05-dbc3dec3e071 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=40a025fd-d1d9-4eac-b304-ab0419714f29 /home           ext3    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=55991bc9-274a-4b01-b14b-b9442ffa24fb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1       /media/Seed     defaults                0       1
/dev/sdb5       /media/Lib      defaults                0       1
```I know I can sudo mount, but I want dev/sda1, sdb5 to mount at boot. 
They're not mounting at boot, and I can't mount them myself without sudo mounting!

---

### Post by jbrown96 on 2009-07-29
You don't have the type included. You need to insert vfat, ntfs, ext3, whatever for those entries.

---

### Post by Elep.Repu on 2009-07-29
> **jbrown96 said:**
> You don't have the type included. You need to insert vfat, ntfs, ext3, whatever for those entries.

Oh ok. Thanks. ;)

---

