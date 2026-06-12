---
title: "Grub loader issue"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by benjit on 2011-01-12
Hi all,

Absolute newbie to linux.  Have just installed Lubuntu, after having seen it on a friends computer.  I like it and would like to learn how to use it, but need the back up of having windows available.  Windows is not appearing in the grub loader menu however.  I know there are a million threads out there about this, but not of them seem to apply (most refer to changing the menu.lst file and I don't have one that I can find!).  I have tried to change the files that generate the grub loader menu choices using leappad, but when i change and try and save them I get a message saying "cannot open file to write"

Anyone any to help with an utter idiots guide to what I should do here, please?

---

### Post by SteveDee on 2011-01-13
> **benjit said:**
> ...Windows is not appearing in the grub loader menu ...

The program that Grub relies upon to looks for existing operating systems is missing from Lubuntu.

Take a look at this: [http://ubuntuforums.org/showthread.php?t=1658838](http://ubuntuforums.org/showthread.php?t=1658838)

---

### Post by benjit on 2011-01-13
Stevedee, you are a star.  Thanks very much for the help.
 
A little strange.  It's added a grub menu item only for "windows recovery partition".  Choosing that chainloads (I think thats the term?) into another boot menu offering Windows or Ubuntu.  On first run, it performed a full checkdisk (I assume this is due to Lubuntu altering partitions), then rebooted, but second time through it's come into Windows fine.  
 
Thanks again.

---

### Post by benjit on 2011-01-13
Another minor problem.  I know I am now meant to mark this thread as solved, but I can't see the option!

---

### Post by Legeril on 2011-01-13
There are options for Thread Options at the top of the thread, one of the options is "mark as solved"

easy and simple when you know how, like most things in Linux :P

---

