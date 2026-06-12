---
title: "My newly created /data partition is not showing in places or media."
date: 2009-11-05
forum: New to Ubuntu
---

### Post by philinux on 2009-11-05
Seems ok from this though.

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=458c5812-6744-4229-b55a-05b143b3e713 /               ext4    errors=remount-ro 0       1
[B]# /data was on /dev/sdb4 during installation
UUID=174b2539-33db-4a11-999e-11152bae5ae7 /data           ext4    defaults        0       2[/B]
# /home was on /dev/sdb3 during installation
UUID=be830508-c4db-4501-87ee-3a2ec63d709e /home           ext4    defaults        0       2
/dev/sdb2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

```
mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb3 on /home type ext4 (rw)
**/dev/sdb4 on /data type ext4** (rw)


```

---

### Post by uberg on 2009-11-05
Can you manually mount it?

---

### Post by philinux on 2009-11-05
Feeling a little dim now. :rolleyes:

It's there as a folder under /.

Just had to create a bookmark for it and chown it from root.

---

