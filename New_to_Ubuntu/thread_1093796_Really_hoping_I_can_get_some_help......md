---
title: "Really hoping I can get some help....."
date: 2009-03-11
forum: New to Ubuntu
---

### Post by svtcobra00 on 2009-03-11
Hey all, I tried to install Mandriva on my desktop on a blank harddrive last nite. The install went south so I figured I would just reinstall windows vista and move on with life. After getting all that reinstalled I found that my Western Digital USB Harddrive file system is now corrupt. Not sure how that happened but it has all my itunes and family photos on it. I read about trying to use the Live CD by Ubuntu to possibly backup the data onto another drive but I cannot mount the external drive. When I type in:

fdisk -l this is the info I get:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 + 8225280 bytes

Device Boot /dev/sdb1
Start 1
End 38914
Blocks 312568832
Id 6
System FAT16

What can I do? I really want to beable to transfer all the data onto a partition on my primary hard drive.

Thanks in advance, Matt

---

### Post by cariboo on 2009-03-12
I would suggest using Vista's disk management tools, from your output the disk has changed to a fat16 partition, I believe Windows can deal with that better than Ubuntu. 

Jim

---

### Post by svtcobra00 on 2009-03-12
Thanks Jim for the advice. I have been working with the Vista tools but still no fix. I really dont want to format the drive. I downloaded some disk recovery demo program and it did find all the music and photos but unless I pay $130.00 for the license it wont actually let me save the data. Plus, it finds it as "File1", "File2","File3" and so forth...Was hoping to get back my original file names as well.

---

### Post by oldos2er on 2009-03-12
Try the program testdisk on the partition. See [http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by bodhi.zazen on 2009-03-12
And with testdisk comes photorec ;)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by svtcobra00 on 2009-03-12
Thanks guys...I'll give it a whirl tonight and post my results.

---

### Post by svtcobra00 on 2009-03-15
> **oldos2er said:**
> Try the program testdisk on the partition. See [http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)


Thank You sooooooo much. This worked perfectly!

---

