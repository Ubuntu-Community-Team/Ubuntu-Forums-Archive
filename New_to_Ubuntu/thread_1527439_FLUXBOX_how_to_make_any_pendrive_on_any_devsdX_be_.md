---
title: "FLUXBOX: how to make any pendrive on any /dev/sdX be mounted?"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-07-09
Hello

I would like to make it automatically; I put 1 , 2 , 3 . ..  severlal pendrives at the same time, and LINUX makes me a /media/pendrive1 
 /media/pendrive2 
 /media/pendriveX whatever X number so that the user can mount it with rox mount.

Is there a program that can handle the /etc/fstab for only vfat pendrives only ??

Does someone know? Too difficult question; I know; requires lot of skills with linux ...

---

### Post by cariboo on 2010-07-09
I'm not sure what you are trying to do. Do you object to the pendrive lablel, and want to use the device label in /media?

---

### Post by frenchn00b on 2010-07-10
> **cariboo907 said:**
> I'm not sure what you are trying to do. Do you object to the pendrive lablel, and want to use the device label in /media?

I would like it creates / removes a lne in fstab automatically:
```
/dev/sdg1/       /media/pendrive1      vfat    user,rw,umask=0000,uid=1000,gid=1000,auto  0    2
```

at pendrives plugging, and adapt it automatically

---

