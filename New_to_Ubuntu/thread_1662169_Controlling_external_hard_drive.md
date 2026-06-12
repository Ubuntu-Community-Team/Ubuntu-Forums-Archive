---
title: "Controlling external hard drive"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by MarekS on 2011-01-07
I've just started using an old hard drive in an external caddie connected to my PC by USB. (I don't boot from it, it's just for storage.) The drive happens to have 3 partitions from a previous life - a Windows one and two Linux. I can access and read all the partitions, but I can delete only from the Windows partition. How do I achieve control over everything? For the moment I want to leave the partitions as they are, but I want full rights to them.

---

### Post by bioterror on 2011-01-08
Is this is a desktop computer and are you going to use this usb-system all the time?

If so, you should add those partitions to /etc/fstab with correct parameters.

[Once again Bodhi seems to give you good advices for this]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by MarekS on 2011-01-08
Because I'd like to use it like a memory stick (with different PCs and laptops) it seems the simplest thing to do is to leave it as it is, and ignore the Linux partitions. So I will use the Windows partition only, which is the one to which I have full rights (not that I did anything to acquire them).

Later I may want to format the entire external disk. If I don't want to go through the mount and fstab stuff, should I format it with a Windows file system?

---

### Post by MarekS on 2011-01-08
I've solved my problem by simply formatting the Linux partitions as FAT, so now I can access and write to them on any system. (It seemed strange to have the permission to format each partition but not to delete files.)

---

### Post by col48 on 2011-01-08
Permission to format but not delete?

You don't need to know how to read the current file system if you are going to wipe it out, but deleting one file without damaging other files needs this knowledge.  Demolishing a whole row of houses, compared with removing one in the middle!

---

