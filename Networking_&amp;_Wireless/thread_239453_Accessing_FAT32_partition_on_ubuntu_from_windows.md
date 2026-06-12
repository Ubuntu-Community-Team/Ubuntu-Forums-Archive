---
title: "Accessing FAT32 partition on ubuntu from windows"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by The Pinny Parlour on 2006-08-19
Hi all,

Have created a FAT32 partition on my ubuntu installation so I can share files between windows and ubuntu.  I can see and access my windows pc but my windows PC can't see ubuntu.  

I have gone: System>Administrator>Shared Folders and tried to change the workgroup under "General Windows Sharing Settings"  and tried sharing a root folder but no luck.  

so how do I get my windows PC to see the FAT32 partition on ubuntu abd be able to read and write to it on both pc's?

Thanks for YOUR help.
Ian

---

### Post by anopheles on 2006-08-19
Hi.

I'm not sure I entirely understand your situation - I think you have two PCs, one running windows, the other ubuntu. OK?
(if not, then you have a dual-boot pc, which is a different problem)

>>> Have created a FAT32 partition on my ubuntu installation so I can share files between windows and ubuntu. I can see and access my windows pc but my windows PC can't see ubuntu. 

First: you dont absolutely need to create a FAT32 partition on your ubuntu box. You can "publish" any directory and let your windows PC see it across the network.

Check the following:
Is the samba demon running on your ubuntu box?
Is samba configured to share the new FAT32 partition?
Is samba in the same workgroup as your windows PC?

or better still: Check out this thread: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by The Pinny Parlour on 2006-08-19
Thanks    will start reading.

---

