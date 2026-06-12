---
title: "same disks for OS and RAID 5?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by anon0 on 2009-01-25
Hi all, I'm looking for an effective implementation of a RAID 5 array where the OS resides on the same disks as those in the array. I've managed to build a RAID 5 array over three disks, but my OS is not in a RAID. 

Given hard drives of equal size, how would you partition the disks to protect the OS with RAID while maximizing usable space for the RAID 5 array? 

I read that you only need a small partition such as 100MB to boot the OS, but how does that work if the Ubuntu installation itself requires over a gigabyte? I'm not sure how /boot works and how to set it up.

---

### Post by tad1073 on 2009-01-25
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://ubuntuforums.org/showthread.php?t=33652](http://ubuntuforums.org/showthread.php?t=33652)

---

### Post by anon0 on 2009-01-26
The following thread covered the same topic, trying to put the root on RAID5 and boot from a non-RAID /boot:
[http://ubuntuforums.org/showthread.php?t=552093](http://ubuntuforums.org/showthread.php?t=552093)

The user ultimately failed to achieve this, however:
[http://ubuntuforums.org/showpost.php?p=3862940&postcount=23](http://ubuntuforums.org/showpost.php?p=3862940&postcount=23)

Has anyone here done it successfully?

---

