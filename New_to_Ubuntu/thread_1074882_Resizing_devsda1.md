---
title: "Resizing /dev/sda1"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Kareeser on 2009-02-19
Quick question...

Given this file structure:
```
/dev/sda1 as ext3, mounted to /
/dev/sda2 as an extended partition, containing
   /dev/sda5 as swap
/dev/sda3 as ext3, mounted to /media/Storage
```

Is there any way for me to integrate sda1 and sda3 into one large partition?

---

### Post by logos34 on 2009-02-19
> **Kareeser said:**
> 
Is there any way for me to integrate sda1 and sda3 into one large partition?

Yes, but you'll have to image root (maybe with gparted or partimage) and copy the files on sda3 to another disk, delete sda1 and sda3, grow the extended to take up the remaining space, and copy the partitions back.  It's not like you can just 'convert' logical or primary partitions into the other

---

### Post by Kareeser on 2009-02-20
Thanks logos34... I thought that may be the case, since I had initially left the partition for a Windows installation that never ended up happenning.

I may as well go for a clean start. Never hurts. :)

---

### Post by jerome1232 on 2009-02-20
This is why I like LVM, you can just add, remove, and resize volumes without regard to disk order and such ;) You can also move Logical Volumes around on different Physical Volumes.

Although there is a small learning curve when learning how to manage them.

---

