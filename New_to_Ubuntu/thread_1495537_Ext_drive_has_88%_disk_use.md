---
title: "Ext drive has 88% disk use"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Franz01 on 2010-05-28
I am using a ubuntu 7 and my machine is Intel pentium 4 based.
I mounted an ext drive fat32 with 
mount -t vfat /dev/sdb1 /media/my_ext_drive

The external drive has 87% use but I removed all the files and directories... 

Anybody can explain why??

output of df command is:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             33506948   6786644  25018220  22% /
...
/dev/sdb1            244136352 211654720  32481632  87% /media/my_ext_drive
```

---

### Post by TheStroj on 2010-05-28
Try formating it. It can be done simply with mouse, or by terminal with 'mkfs' command.

---

### Post by mike555 on 2010-05-28
check trash on external....

---

