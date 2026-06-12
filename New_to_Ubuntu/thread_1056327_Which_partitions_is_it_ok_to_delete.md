---
title: "Which partitions is it ok to delete?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by fatherdaly on 2009-01-31
I have a dual boot with ubuntu and vista. Here are my partitions:

[[IMG]http://img91.imageshack.us/img91/4746/discsbz5.th.jpg[/IMG]](http://img91.imageshack.us/my.php?image=discsbz5.jpg)

The ~60gb partition is the main one that ubuntu uses. Is grub on this partition or one of the smaller ones? Because I need to delete the 60gb partition for more room and I don't want to wipe grub because then nothing will boot (I've done that before#-o)

---

### Post by jbrown96 on 2009-01-31
Are you getting rid of Ubuntu? If you are, then you don't need to have grub at all. If you login into the recovery console in Windows (press F8 during boot) and do fixmbr (I think), then you won't need grub. 

If you are going to replace Ubuntu with another distro, then it will reinstall Grub and you will be fine.

---

### Post by ajgreeny on 2009-01-31
Grub would appear to be on your OS (:C) partition, which you will see is your boot partition.  However, what are you trying to do?  Even if you leave grub on the partition but delete the ubuntu partition, you will not be in any better a situation as your menu.lst file will be gone and grub will be useless.

More information please about your intentions.

---

### Post by fatherdaly on 2009-01-31
Basically I just want to free up some room by deleting the ubuntu partition but I'm concerned that by doing so I will not be able to boot anything.

---

### Post by bruce89 on 2009-01-31
> **fatherdaly said:**
> Basically I just want to free up some room by deleting the ubuntu partition but I'm concerned that by doing so I will not be able to boot anything.

Indeed, you can reinstall the Windows bootloader using the Windows CD's recovery mode.

---

### Post by louieb on 2009-01-31
To be sure boot to Ubuntu and list your partition table that way.  Can't  tell where grub is by looking at disk management in windows. 
```
sudo fdisk -l 
```lowercase L at the end also post the output of ```
mount
```

Guess its in the 50+GB partition. One of smaller 2+GB partition is probably swap and who knows what the other is.
any way this will help you out. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

