---
title: "[SOLVED] Quota"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by 007casper on 2008-12-03
installing this server set up...
[http://howtoforge.com/perfect-server-ubuntu-8.10-p4](http://howtoforge.com/perfect-server-ubuntu-8.10-p4)

can someone tell me what the quota is on step 12?

and what am I suppose to write for /etc/fstab

I have partition my hard drive as 
ext3 / 30 gb
ubuntu /home 450 gb
swap 20.3 gb

thank you

---

### Post by nhasian on 2008-12-03
in your /etc/fstab you need to edit the line for your /home directory.

your options for /home now probably look something like:

```
ext3    relatime,errors=remount-ro 0       1
```

you need to make it say:

```
ext3    relatime,errors=remount-ro,usrquota,grpquota 0       1
```

also take a look at my thread here:

[http://ubuntuforums.org/showthread.php?t=996603](http://ubuntuforums.org/showthread.php?t=996603)

---

### Post by 007casper on 2008-12-03
I dont have
```
ext3    relatime,errors=remount-ro 0       1
```

for /home I got...
```
ext3    relatime 0       2
```



relatime,errors=remount-ro,usrquota,grpquota 0 2

what is 2?  should I change it to 1

---

### Post by nhasian on 2008-12-03
according to [http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

the last two numbers refer to [dump] and [fsck order]

Dump: Dump field sets whether the backup utility dump will backup file system. If set to "0" file system ignored, "1" file system is backed up.


Fsck: Fsck order is to tell fsck what order to check the file systems, if set to "0" file system is ignored.

so i guess you should leave them the same as you already have.  just add the *usrquota,grpquota* to the options.

---

