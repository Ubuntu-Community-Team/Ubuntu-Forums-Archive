---
title: "Gnome's System monitor is calling Windows partition &quot;fuseblk&quot; filesystem."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Pogeymanz on 2009-02-08
If I open system monitor and click the filesystems tab, it has / as reiserfs, and /home as ext3, which is exactly what they are. But it also has /windows as fuseblk. Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=6e5963cc-ba1c-4713-8f6c-4a91ac21ec06 /               reiserfs notail,relatime 0       1
# /dev/sda7
UUID=56214851-f699-43d6-9527-ac8550a5ece6 /home           ext3    relatime        0       2
# /dev/sda5
UUID=82ac1361-72af-499e-a511-64bb65a51e42 none            swap    sw              0       0
# /dev/sdb1
UUID=77e01bb2-abce-46c2-b27c-9a674472fd4b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/sda2
/dev/sda2       /windows     ntfs-3g     defaults,locale=en_US.UTF-8    0      0
```

---

### Post by k3rnelmustard on 2009-02-08
FUSE is Filesystem in USErspace.  It is what ntfs-3g uses.  FUSEBLK just means it's a FUSE filesystem.  (ZFS or SSHFS running with FUSE would show up the same way)  It's totally normal.

---

### Post by drs305 on 2009-02-08
That is a normal listing. FUSE (Filesystem in Userspace) creates a block device to mount NTFS partitions.

---

### Post by Pogeymanz on 2009-02-08
Great. Thank you.

---

