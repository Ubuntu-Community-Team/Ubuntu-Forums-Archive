---
title: "how do i boot off an external drive?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by HTMLCrazy on 2011-01-21
I am trying to boot a backtrack4 live dvd, but i do not have an internal drive and my computer does not support usb boot. is there any way to boot a bootable dvd from ubuntu?

---

### Post by Verbeck on 2011-01-21
> **HTMLCrazy said:**
> is there any way to boot a bootable dvd from ubuntu?
yes, virtualization
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by ajgreeny on 2011-01-21
> **Verbeck said:**
> yes, virtualization
[http://www.virtualbox.org/](http://www.virtualbox.org/)
But not if there is no internal drive!

To OP:-
Does the computer have a floppy drive?  If so you may be able to use supergrub, to boot from the floppy and then pass the boot to the USB drive.

I think I have heard of it being done that way in the past, but can't give you anymore info, and it is such a long time since I saw anything about supergrub that things may have changed totally now.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

PS:  Just a thought:  do you mean no internal CD/DVD drive?  If so ignore this; you can use virtualisation!

---

### Post by HTMLCrazy on 2011-01-21
> **ajgreeny said:**
> But not if there is no internal drive!



PS:  Just a thought:  do you mean no internal CD/DVD drive?  If so ignore this; you can use virtualisation!

How do you use virtulisation?

---

### Post by ajgreeny on 2011-01-21
Install VirtualBox from Oracle, and then follow the instructions, which you can get from Oracle as well, to install a virtual machine from the usb install disk.

---

### Post by HTMLCrazy on 2011-02-06
Thanks a lot!! It worked!

---

