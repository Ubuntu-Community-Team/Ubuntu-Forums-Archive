---
title: "resizing partition"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Velenjak on 2010-11-09
hello.

I currently run windows 7 w/ wubi. When I initially installed wubi I did not assign enough partition space to its section. I use ubuntu as my primary OS. How do I go about adjusting the space designated to ubuntu? I've read some how-to articles but to be honest the terminology and instructions are over my head.... thanks much!

---

### Post by toekneewood on 2010-11-09
Take a look at gparted.  You can download a ISO image and burn it onto a CDROM.  You should then be able to boot of the CDROM and get access to the partitions.  Please remember to back up your data.  These sort of changes can be a bit hit and miss.

---

### Post by Gremlinzzz on 2010-11-09
Why not just uninstall then reinstall with wubi?
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2010-11-09
I've heard that lvpm still works to resize wubi root.disk partitions. 

Lvpm's other functions won't work (to migrate a wubi install), and it will install with broken dependencies since it requires grub (legacy) not grub-pc (grub2). 

Note that the resize doesn't increase the root.disk size, it creates a new one.and copies the data from the old to the new. It assumes the ext3 file system although current installs use ext4.

---

### Post by bcbc on 2010-11-09
> **Gremlinzzz said:**
> Why not just uninstall then reinstall with wubi?
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

WARNING - uninstalling will delete all your data and settings on Ubuntu

---

### Post by Mark Phelps on 2010-11-10
> **toekneewood said:**
> Take a look at gparted.  You can download a ISO image and burn it onto a CDROM.  You should then be able to boot of the CDROM and get access to the partitions.  Please remember to back up your data.  These sort of changes can be a bit hit and miss.

Guess you entirely missed the part where the OP mentioned Wubi??

Next time, read more carefully before offering advice.

---

