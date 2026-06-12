---
title: "Mounting my hard drive"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by greenfuzz on 2009-03-18
Hi, I installed Ubuntu onto a Vista hard disk, but the remaining partition is inaccessible and unmountable from what I can determine. This started as soon as I'd got the internet up and running on my machine under ubuntu, prior to that I could access both the Windows partition and my iPod, now both are inacessible icons in "Computer"  irrespective of my efforts to mount through terminal, and giving myself full priveliges. I'm certain there's a way to fix this, I just doubt it involves my computer, a window and a passing car.

....help??!?!!?!

---

### Post by DaveG825 on 2009-03-18
Have you looked at the partitions in gparted? You may have certain tags or settings on some of your partitions that are preventing you from doing what you want.

---

### Post by kansasnoob on 2009-03-18
Try installing ntfsprogs either from synaptic or go to terminal and run:

```
sudo apt-get install ntfsprogs
```

An option is ntfs-config but I prefer ntfsprogs. You should know that allows access to everything on the ntfs partition so you can destroy things if you're reckless! (Like program files)

---

### Post by ajgreeny on 2009-03-18
Can you show the output of the command ```
sudo fdisk -l
``` and ```
cat /etc/fstab
``` and tell us which partitions are not accessible to you from ubuntu, though it will probably be obvious which is your windows partition.

PS:  Did you install using wubi?  I ask this as I don't know anything about wubi in detail and it will need others to tell you more, if that was the case.

---

