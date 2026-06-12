---
title: "i can't delete &amp; create Folders in partition"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by mahmoud fayed on 2010-06-24
[LEFT][SIZE=4]hi all 
i can't delete files or folders and  ''create Folders'' is not Active 

[IMG]http://img59.imageshack.us/img59/8651/screenshotjp.jpg[/IMG]

[IMG]http://img685.imageshack.us/img685/2171/screenshot1eo.jpg[/IMG]

so how to give users Permissions to read and write in partitions 


Thanks
[/SIZE][/LEFT]

---

### Post by Diabolis on 2010-06-24
You can right click the sda3 folder and set the permissions. I'm guessing that you don't own that folder, probably root is the owner. By just changing that you'll get all the permissions that you need.

---

### Post by oldfred on 2010-06-24
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Letting the system automount often does not give full rights. Also what file system is it, ext3 or 4 or NTFS?

To see permissions from directory above your mount:
```
ls -l
or
 ls /media -l
```

---

