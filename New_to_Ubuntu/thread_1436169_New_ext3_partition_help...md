---
title: "New ext3 partition help.."
date: 2010-03-22
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-22
I have created new ext3 partition using Gparted to store my datas.But i cant able to create files or paste files in this partition..How to fix this?

---

### Post by sylaryn on 2010-03-22
Have you mounted the partition? If so, is it mounted read-only?

---

### Post by Gone fishing on 2010-03-22
I do this with a nice hand crafted fstab - but there is an easy way

sudo apt-get install mountmanager

Then System > administration > Mountmanager

enjoy

---

### Post by psusi on 2010-03-22
By default a newly formatted partition's root directory is owned by root and only writable to root.  You need to change the permissions.  If it is mounted in /media/sda3, then in a terminal do sudo chown o+rw /media/sda3.  This will allow everyone read and write access.

---

### Post by Gone fishing on 2010-03-22
Ooopps sorry

---

### Post by bodhi.zazen on 2010-03-22
> **psusi said:**
> By default a newly formatted partition's root directory is owned by root and only writable to root.  You need to change the permissions.  If it is mounted in /media/sda3, then in a terminal do sudo chown o+rw /media/sda3.  This will allow everyone read and write access.

s/chown/chmod

and you need x for directories ...

sudo chmod o+rwx /media/sda3

for details, see

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Paqman on 2010-03-22
If you don't fancy fiddling about in the terminal, you can install pysdm to set up your partition.

---

### Post by psusi on 2010-03-22
Ooops, yea... I have a little dyslexia with chmod/chown.  Think the right one in my head and my fingers type the other.

---

### Post by karthick87 on 2010-03-23
> **bodhi.zazen said:**
> s/chown/chmod

and you need x for directories ...

sudo chmod o+rwx /media/sda3

for details, see

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")


This helped me thanks a lot :)

---

### Post by karthick87 on 2010-03-23
I have no files in this new ext3 partition but my Disk Properties shows that i have used 649.8MB..Why n what may be the reason?

---

### Post by psusi on 2010-03-23
If you just cleanly formated it then it is filesystem overhead.  I think the two largest offenders that you might try tweaking are the size of the journal and the resize inodes.  By default plenty of space is reserved by the resize inode so you can increase the size of the fs on the fly in the future.  You can try telling mke2fs not to create the resize inode.  Also by default 5% of the space is reserved for root to prevent other users from filling up the disk and causing problems when things like the system logger can't write to the disk.

---

### Post by karthick87 on 2010-03-27
> **psusi said:**
> By default a newly formatted partition's root directory is owned by root and only writable to root.  You need to change the permissions.  If it is mounted in /media/sda3, then in a terminal do sudo chown o+rw /media/sda3.  This will allow everyone read and write access.


How to change it back to the original form?

---

### Post by s_ø on 2010-03-27
I would recomend you read the documentation about file permissions. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Its easy to get confused in the beginning.

To change it back to its original form you need to know what original form is.

If you want to see permissions and ownership use the terminal.
Change directory to /media.
```
cd /media
```
then
```
ls -l
```

---

