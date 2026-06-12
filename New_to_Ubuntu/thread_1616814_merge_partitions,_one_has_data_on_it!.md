---
title: "merge partitions, one has data on it!"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by mikee55 on 2010-11-08
Hi Everyone, please could you turn my mess into 1 partition? Thing is
/dev/sda5 has data on it, I don't have a big enough drive to back it up.

[[IMG]http://img100.imageshack.us/img100/6834/screenshotlu.th.png[/IMG]](http://img100.imageshack.us/i/screenshotlu.png/)


What do I do, DiskDoctors:confused:?

Mike

---

### Post by TeoBigusGeekus on 2010-11-08
Unmount both partitions, sda5 and sda3, then right click sda3>delete.
After that, right click sda5>resize.

Whatever you do, make sure you don't interrupt gparted during the procedure.

---

### Post by mikee55 on 2010-11-08
Nothing to resize???

[[IMG]http://img576.imageshack.us/img576/5467/screenshot1jy.th.png[/IMG]](http://img576.imageshack.us/i/screenshot1jy.png/)


Mike:)

---

### Post by arpanaut on 2010-11-08
You are going to have to first merge/enlarge the unallocated space into the extended part. sda2.
Then enlarge the sda5 part. It has no space to enlarge into at present, the extended container/part. is not large enough.

PS this is going to take a LONG time be prepared... If a laptop be plugged in, Make sure of NO power interruptions in any case!

---

### Post by mikee55 on 2010-11-09
It won't let me do that!!!

Mike

---

### Post by TeoBigusGeekus on 2010-11-09
Format the unallocated space to ext4.

---

### Post by Mark Phelps on 2010-11-09
You have to resize the Extended partition first -- sda2.  Then, you can resize the partition inside it -- sda5.

---

