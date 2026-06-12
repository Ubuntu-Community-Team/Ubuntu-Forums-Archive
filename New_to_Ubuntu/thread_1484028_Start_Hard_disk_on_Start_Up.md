---
title: "Start Hard disk on Start Up?"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-05-15
I am running Ubuntu 10.04 alongside Windows 7 Pro and I can access all my Windows files in Ubuntu. However, to access them, I have to open a second hard disk in My Computer which also mounts it to the Desktop. Is there a way to start this hard disk at start up and without mounting it to the Desktop, somewhat like privately? The only reason why I ask is cause I access all my music and videos in Windows instead of eating up space in Ubuntu, so it's a space safer for me I guess. :)

---

### Post by Elfy on 2010-05-15
Add the drive to fstab - manually or with one of the GUIs - there is ntfs-config or pysdm to my knowledge.

[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by cgroza on 2010-05-15
You have to edit your fstab... If the partitions are NTFS you can use ntfs-config (its in the repositories) to configure it...

---

