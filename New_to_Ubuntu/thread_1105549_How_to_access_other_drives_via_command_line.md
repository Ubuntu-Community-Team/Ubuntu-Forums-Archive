---
title: "How to access other drives via command line?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by wlan-11g on 2009-03-24
I can access the main drive containing the /home folders etc..

But I had 3 other drives that I would like to access via CMD

---

### Post by oldos2er on 2009-03-24
You need to know the mount points of the disks, e.g.
```
cd /media/disk-1
```
for example.

---

### Post by blueridgedog on 2009-03-24
You can issue the mount command to see where the drives are mounted:

```
blueridge@Ripstop:~$ mount
(system stuff deleted)
/dev/sda3 on /documents type vfat (rw,utf8,umask=007,gid=1000,uid=1000)
/dev/sdb1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/scd1 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=james)
blueridge@Ripstop:~$
```

Then:
```

cd /documents
```

(in my case)

---

### Post by SuperSonic4 on 2009-03-24
Mount points are also defined in /etc/fstab which can also be used for automounting on boot.

```
/dev/sda1 on /media/Videos type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /media/Music type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /media/Documents type fuseblk (rw,allow_other,blksize=4096)
/dev/sda4 on /media/Pictures type fuseblk (rw,allow_other,blksize=4096)
/dev/sdd1 on /media/KINGSTON type vfat (rw,noexec,nosuid,nodev,fmask=0133,dmask=0022,uid=1000)
/dev/sr1 on /media/CDROM type iso9660 (ro,noexec,nosuid,nodev,mode=0444)
```

so in my case it would be ```
cd /media/Documents
```

---

### Post by wlan-11g on 2009-03-24
Thanks guys!

---

### Post by blueridgedog on 2009-03-25
One note:  If the drive is automatically mounted, as in the case of external media, it will not be in /etc/fstab

---

### Post by t0p on 2009-03-25
FYI, it is not CMD!  It's the terminal/console/command-line.

---

