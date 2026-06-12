---
title: "Copy hard drive"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by bobandirus on 2009-11-25
Is it possible to do a carbon copy, as it were, of the Ubuntu partition of my hard drive, onto a USB hard drive? Whenever I try and just copy paste, it comes up with a lot of errors. I'm using 8.4.

---

### Post by wojox on 2009-11-25
Check out Clonezilla.

---

### Post by doas777 on 2009-11-25
it is possible to copy a partiton, but no, your plan will not work as such. there is more on the hdd than just your files, so you can't just copy them, and a partition image, will not work unless the usb disk has the same geometry as your hdd. additionally, since many of the constants will have changed (which disk the mbr and boot loader are on, etc) so you would ahve to perform signifigant manual reconfiguration to make it work.

instead I would either install it onto your thumb, or look into System -> Administration -> USB Startup Disk Creator

---

### Post by bobandirus on 2009-11-25
Clonezilla looks to be precisly what I want :) Im assumeing it works easily in Ubuntu?

---

