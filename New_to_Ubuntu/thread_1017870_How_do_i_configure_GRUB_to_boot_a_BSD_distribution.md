---
title: "How do i configure GRUB to boot a BSD distribution?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by GutsyRabbit on 2008-12-21
Hi, dear Ubuntu users.
I have litle problem, i stalled today my first BSD type distribution, and now i wonder, how to configure the GRUB bootloader from Ubuntu to boot BSD.
 P.S.: The name of this distro is PC-BSD and i use Ubuntu Studio, among other 4 linux distributions. Can't wait to test it. :popcorn:

Thanks in advance :KS

---

### Post by logos34 on 2008-12-22
try this:

list your hdd partitions and find your pc-bsd / #:

sudo fdisk -l
e.g.: pc-bsd is sda3 (or in grub-speak, 'hd0,2'):

gksudo gedit /boot/grub/menu.lst

add this entry to bottom:

> title PC-BSD 
root (hd0,2,a)
kernel /boot/loader
boot

or else try 'chainloader' entry:

> title PC-BSD 
rootnoverify (hd0,2) *or just 'root'
chainloader +1
boot 

*you may also need to write grub code to pc-bsd / partition for chainloader to work:

> sudo grub

grub> root (hd0,2)
grub> setup (hd0,2)
grub> quit

[http://faqs.pcbsd.org/index.php?action=artikel&cat=16&id=10&artlang=en](http://faqs.pcbsd.org/index.php?action=artikel&cat=16&id=10&artlang=en)

---

### Post by GutsyRabbit on 2008-12-24
i Will try your method in a few hours, after i'm done i will tell you if it works.

Right now i got math tests :(

---

### Post by GutsyRabbit on 2008-12-30
Thanks for the help, it worked but i uninstalled that BSD distribution, BSD has to have more years of development until it's ready for my IT needs.

---

### Post by Bachstelze on 2008-12-30
> **GutsyRabbit said:**
> Thanks for the help, it worked but i uninstalled that BSD distribution, BSD has to have more years of development until it's ready for my IT needs.

Yeah, right. May I ask what kind of "IT needs" you have?

---

