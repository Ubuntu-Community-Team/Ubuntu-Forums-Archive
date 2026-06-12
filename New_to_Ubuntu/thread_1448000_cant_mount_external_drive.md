---
title: "cant mount external drive"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by theshaggy69 on 2010-04-06
Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I get this when I try to mount this drive. I was working just fine and then when I tried to mount again to pull some data off It gave me an error. It is an internal hard sata hard drive hook up via usb with a usb to sata converter. Is there some kind of disk check i can do to find errors. There is data on there I would like to keep 
PLEASE Help!!!!!!

---

### Post by @rizz on 2010-04-06
hi,

for check disc

if your disk is serial ata:
 

 Disk ID: [s or h]d[a..z][number of partition]


That is in your case```
$ sudo fsck /dev/sdb1
```

---

### Post by theshaggy69 on 2010-04-06
Thank you so much that worked. I ran and it said file system was clean and was able to mount

---

### Post by @rizz on 2010-04-06
Glad to help!):P

---

