---
title: "Partition crash"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by novice1969 on 2011-02-22
I have a dual boot system

I updated all the latest updates. On completion, after the intall process I was asked to reboot.

During the reboot (fairly early) my system stopped with the following:

mount: mounting /dev/disk/by-uuid/e4a29af8-44fa-4cde-9495-f602bc537be3 on /root
failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootarg

Bysybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands


What is this?  How do I get Ubuntu to boot or do I have to rebuild system?

---

### Post by Ben Page on 2011-02-22
Have you manually added these folders to automount at startup? Have you edited the /etc/fstab file? Ca you see the content of the fstab file?

You can access it from CLI

```
sudo nano /etc/fstab
```

or via live CD

---

### Post by novice1969 on 2011-02-22
I have a live CD and when I put the command "sudo nano /etc/fstab" in the command line I get the following response:

aufs/ aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sda7 swap swap defaults 0 0


What does that all mean?

---

