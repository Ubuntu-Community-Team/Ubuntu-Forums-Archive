---
title: "error:formatting pendrive using gparted"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-12-24
I got an error while formatting the pendrive,and it happend like this 
when i tried to format(to ext3) the pendrive using gparted it is saying that
[ATTACH]97446[/ATTACH]

please any one help me in this :confused:

---

### Post by LowSky on 2008-12-24
this happens every once in a while, and using EXT3 on a pendrive is not great becasue journaling is unrequired.

EXT2 or FAT32 (if you need windows support) are better options.

Just reboot your machine, and you will be able to continue the reformat

---

### Post by taurus on 2008-12-24
You need to unmount the drive first before you can format it.

Applications -> Accessories -> Terminal
```
sudo umount /dev/sdb5
```
Now, restart gparted.

---

### Post by phanipalagummi on 2008-12-24
thank you guys you all are rocking.:guitar:

merry christmas guys

---

### Post by prathyush on 2011-10-12
hi,

i get the below error:

umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
i have tried fuser /dev/sda8, but not able to get any output

---

