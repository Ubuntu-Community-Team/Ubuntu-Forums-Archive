---
title: "share backup drive with windows machine"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by spaulson on 2006-08-27
I have and external hard drive that is connected to my ubuntu computer.  It is used for the purpose of backing up and has several partitions.  One of the partitions is NTFS which I would like to share such that my windows machine (separate unit) can back up to it.

Is this even possible?  If so any pointers on how do to this would be helpfull

thanx

---

### Post by kotnik on 2006-08-27
Yes, sure it's possible.

Use ntfs-3g driver to mount RW yours NTFS partition, and Samba to share it with Window$ machine.

---

### Post by spaulson on 2006-08-27
thank you

---

