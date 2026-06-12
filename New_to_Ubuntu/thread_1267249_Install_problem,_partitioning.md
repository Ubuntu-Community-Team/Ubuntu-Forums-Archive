---
title: "Install problem, partitioning"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by paneity on 2009-09-15
Hi, 
I'm trying to set up a dual boot with vista and 9.04. When I tried to install just now, I got to the manually edit partition page, but on the list of disks, my hard drive had free space as unknown, and when I tried to edit it I couldn't resize it. (My recovery partition was listed with the amount of free space, and could be edited)

Any ideas why this is? My hard drive has been defragmented, and has over 50GB of free space.

Help much appreciated.

---

### Post by bacardiandwatermelon on 2009-09-15
ummm what do the partitions on the drives look like?

---

### Post by soldier4jesus on 2009-09-15
You may want to try to partition your hard drive in Vista.  Here's a link that will give you an easy way to do it.

[http://techblissonline.com/vista-partition-drive-disk-volume/](http://techblissonline.com/vista-partition-drive-disk-volume/)

God Bless!!
Wes

---

### Post by paneity on 2009-09-15
> **bacardiandwatermelon said:**
> ummm what do the partitions on the drives look like?

Not sure what you mean, there are 2 partitions on the hard disk, C: about 140GB which has vista on it, and a recovery partition D: which is 8GB. On the partition edit screen, from memory, C: was in green, D: in orange, I thought this was just to distinguish the two.

---

### Post by paneity on 2009-09-15
> **soldier4jesus said:**
> You may want to try to partition your hard drive in Vista.  Here's a link that will give you an easy way to do it.

[http://techblissonline.com/vista-partition-drive-disk-volume/](http://techblissonline.com/vista-partition-drive-disk-volume/)

God Bless!!
Wes

Yeah, this says it will only allow me to shrink by 664MB, with the message about pagefiles etc, would these also affect the ubuntu partitioner?

---

### Post by bacardiandwatermelon on 2009-09-15
partition magic can shrink your vista partition without losing data (unless it breaks), its a windows app, have used it heaps before...

---

### Post by oldfred on 2009-09-15
If problems in shrinking using Vista's partitioner, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
Defrag twice. 
You may still have to try to shrink partway then defrag again.

---

