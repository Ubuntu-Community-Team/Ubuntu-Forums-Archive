---
title: "partition not in fstab but still mounted automatically?"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by FreeTheBee on 2010-05-16
Hi, today I converted a partition from ntfs to ext4. After changing fstab and the proper permissions everything seemed fine except the partition was not mounted in the folder I specified in fstab.
Just to test I commented out the line regarding this partition in fstab and rebooted. The partition still gets mounted automatically and, after changing its label with disk utility, even the right place.
In a way really nice of course, because all works fine. But I wondered what is controlling this. Does anyone know?

---

### Post by -humanaut- on 2010-05-16
I have a similar situation with a fat32 partition I have that I don't want mounted unless its necessary I like that when I need it it's just a click away but it doesn't have an fstab entry either every other distro I've used I needed to add it. (It's a backup partition pretty much a separate /home with important files)

---

### Post by cuberts on 2010-05-16
> **FreeTheBee said:**
> Hi, today I converted a partition from ntfs to ext4. After changing fstab and the proper permissions everything seemed fine except the partition was not mounted in the folder I specified in fstab.
Just to test I commented out the line regarding this partition in fstab and rebooted. The partition still gets mounted automatically and, after changing its label with disk utility, even the right place.
In a way really nice of course, because all works fine. But I wondered what is controlling this. Does anyone know?
yes it is probably correctly mounted automatically

---

### Post by FreeTheBee on 2010-05-16
It seems it happens to others as well,
[http://ubuntuforums.org/showthread.php?p=9278984#post9278984](http://ubuntuforums.org/showthread.php?p=9278984#post9278984)

didn't find this before. It is of course no problem as long as all works fine, but I am just curious to know where these things are set, if not in fstab.

---

