---
title: "Lock files"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-12-31
i have tried 

```
sudo chown -R deadlysniper:deadlysniper /media/disk
```

I get an access error every time I do it. I am trying to change the access to deadlysniper so that way I can open, read, and write

---

### Post by Martje_001 on 2008-12-31
Can we see your fstab?

---

### Post by s3a on 2008-12-31
This isn't a direct solution to your problem but there is a GUI application for this (in the universe repository):

sudo apt-get install cryptkeeper

---

### Post by Michael.Godawski on 2008-12-31
hi,

additionally to the fstab file

```
cat /etc/fstab
```

can you also post

```
ls -la /media
```

---

### Post by deadlySniper on 2008-12-31
## /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=89939b6c-0c01-41a3-b950-0c6a9e371836 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0ea98489-c072-4b3f-ba3a-9591b95dca17 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


total 64
drwxr-xr-x  5 root         root  4096 2008-12-31 01:26 .
drwxr-xr-x 20 root         root  4096 2008-12-23 18:27 ..
lrwxrwxrwx  1 root         root     6 2008-12-23 13:14 cdrom -> cdrom0
drwxr-xr-x  2 root         root  4096 2008-12-23 13:14 cdrom0
drwx------  8 deadlysniper root 16384 1969-12-31 19:00 disk
-rw-r--r--  1 root         root   226 2008-12-31 01:26 .hal-mtab
-rw-------  1 root         root     0 2008-12-30 13:30 .hal-mtab-lock
drwx------  5 deadlysniper root 32768 2008-12-31 00:16 IOMEGA HDD

---

