---
title: "[SOLVED] partition help"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by som1special2 on 2008-12-06
Have a laptop with a 40 gb hard drive. I have Windows XP on the larger portion and ubuntu on the smaller. 35/5 split. I downloaded the partition manager and want to know if I can delete windows and re-allocate the unused space to ubuntu without having to re-install ubuntu. If so how do I do it with the partition manager? thanks in advance

---

### Post by Yuki_Nagato on 2008-12-06
You will want a second opinion on this.

First, backup.

Then go to this website and download and burn this program to CD.

_[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)_

This will allow you to boot back into Ubuntu when we mess up the partitions.

Now you can open up the partitioner and expand the Ubuntu partition to include the entire disk.

Upon resetting, GRUB will throw a fit because the starting blocks of the partitions moved around, and you would be stuck otherwise.

Restart, and boot to the Super GRUB disk instead.  This program should allow you to reinstall GRUB with some basic settings.  In other words, it should be able to create enough of a configuration for you to boot into Ubuntu, and edit any else you want to from there.

---

### Post by ranch hand on 2008-12-06
Are you talking about gparted as partition manager?  If so, yes you can do this.  It would be a VERY good idea to back up your system before doing so.

You must have an Ubuntu swap partition too.

Take a look at things in your partition manager and let us know - is it gparted (or what) and do you have 2 or actually 3 partitions.

---

