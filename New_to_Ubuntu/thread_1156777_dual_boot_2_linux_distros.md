---
title: "dual boot 2 linux distros"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by 5mattyb5 on 2009-05-12
Hi all I wouldn't really consider myself a newbie anymore, but I've got an issue I've never ran into before.  I just got a new computer and it has 2 hard drives, my objective is to install ultimate edition on one which was successful and sabayon on the other, which was successful. However after installing sabayon on a completly different drive I could only boot into sabayon.  Did I do something wrong in the installation, maybe I should not have formatted the bootloader.  Just for the record I use gparted to view my drives and the 2 operating systems were indeed on seperate drives.

---

### Post by ashmew2 on 2009-05-12
Hi , 

Sabayon uses Grub as well , Right ?

So , all you need to do is add a Grub entry to the /boot/grub/menu.lst file for booting into Ubuntu.

Take a look here : [http://ubuntuforums.org/showthread.php?t=219745]("http://ubuntuforums.org/showthread.php?t=275728")

It's for adding Vector Linux to the menu..You can just boot into Sabayon and do as they describe on the thread :D

---

### Post by ashmew2 on 2009-05-12
-Duplicate-

---

### Post by longtom on 2009-05-12
I agree with ashmew2.

What possibly happened here, is, that Sabayon didn't pick up your Ubuntu install (maybe, because it was on a different drive).

Just get the exact location of your install and add an entry to the menu.lst.

Good luck

---

### Post by 5mattyb5 on 2009-06-04
Thanx for the replies guys but I gave up with one grub and now just have a seperate grub on each drive.

---

