---
title: "/disk"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2009-12-01
i'm not able to save anything on the desktop or my home directory i'm getting the error message that / disk is ful. please help me out of this problem

thank you

---

### Post by ukripper on 2009-12-01
post output of this command:
```
df -h
```

---

### Post by 1991sudarshan on 2009-12-01
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10            2.3G  2.3G     0 100% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  108K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  172K 1002M   1% /dev
tmpfs                1003M  244K 1002M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M  1.0M     0 100% /tmp
/dev/sda5              59G   29G   31G  48% /media/disk
/dev/sda6              64G   35G   29G  55% /media/disk-1

---

### Post by ukripper on 2009-12-01
> **1991sudarshan said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10            2.3G  2.3G     0 100% /


Self explanatory error you got before, as you can see your root (/) is used as 100%. Why you only using 2.3 gb? you need atleast 4GB to play ubuntu around.

if you clear some stuff from home and do some autoclean it should free up some space. But it will be hassle for you always until you increease the size of your partition.

---

### Post by 1991sudarshan on 2009-12-01
i'm a beginner just tell me out to resize the partion

---

### Post by ukripper on 2009-12-01
Boot into live cd  and follow this guide - [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

there are so many youtube videos too if you need video help.

---

