---
title: "Replacing Mepis with Ubuntu in vista dual boot system"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by AbsolutMayhem on 2009-11-24
Hi. I currently have a Vista/Mepis dual boot system.  Each OS has its own drive (two hard drives). Currently, the system defaults to the linux OS. On the Mepis login screen, the option to load vista is via something called "longhorn loader". 

Grub is already in place on my system. I want to use Ubuntu instead of Mepis as my linux os. Can I just use the Ubuntu live CD to install it to the appropriate disk? Will my current grub be wiped out and replaced? During the install will Ubuntu call the disks the same name as Mepis currently does? I'm a little wary because I'm not sure what the longhorn loader thing is. Just want to make sure I'm doing the right thing.

Thanks.

---

### Post by cariboo on 2009-11-24
> **AbsolutMayhem said:**
> Hi. I currently have a Vista/Mepis dual boot system.  Each OS has its own drive (two hard drives). Currently, the system defaults to the linux OS. On the Mepis login screen, the option to load vista is via something called "longhorn loader". 

Grub is already in place on my system. I want to use Ubuntu instead of Mepis as my linux os. Can I just use the Ubuntu live CD to install it to the appropriate disk? Will my current grub be wiped out and replaced? During the install will Ubuntu call the disks the same name as Mepis currently does? I'm a little wary because I'm not sure what the longhorn loader thing is. Just want to make sure I'm doing the right thing.

Thanks.

The install will over write your mepis install. Mepis is based on Debian, the same as Ubuntu, so you shouldn't have any problems with disk id's. 

Longhorn, is what Vista was called before release. on my system the menu entry is "Windows Vista (loader) (on /dev/sdb2)"

---

