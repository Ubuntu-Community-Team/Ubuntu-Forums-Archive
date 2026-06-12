---
title: "Error booting Ubuntu 10.4 beta2"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Bkock on 2010-04-15
I have installed ubuntu 10.4 beta 2 on a very basic AMD 1900+ CPU with  500MB
of RAM and a 160gb western digital HD. When loading I receive the  following 
ERROR. 
-- I have noticed this problem has occurred in many previous versions.  --

1. Any thoughts as to whether on not this will be fixed in the final  release??

2. I have read fixes for previous versions with a different ver.GRUB,  which 
   the GRUB required modification. What is the current thoughts for a  fix
   in ubuntu 10.4 Please make it detailed as I am avid Windows user  (sorry)
   but VERY new to Linux but willing to give it a try.
 
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)

ALERT! /dev/disk/by-uuid/fc2a95-a209-4e07-8d7c-ff84b2e5b531 does not  exist. Dropping to a shell

(initramfs)

---

### Post by Jon Monreal on 2010-04-16
I've had the same problem before.

Do you have a Live CD you could boot from.

If so, please use that, open a terminal window, type the following, and post the output here:

sudo fdisk -l

Thanks.

---

### Post by Bkock on 2010-04-25
I am able to get into Ubuntu now by editing the grub , (changing root=UUID##### to root=/dev/sda1)
When I close Ubuntu and reopen the info was not saved.  I quess my question now is how do I save this data?

Thanks for the help

---

### Post by Jon Monreal on 2010-04-25
Take a look at [the wiki]("https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD") for information on recovering grub.

---

