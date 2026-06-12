---
title: "ATI x1300 problems"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by nitsur on 2009-03-04
I have a dell e1505 running ubuntu 8.04. I have full screen resolution with my graphics driver disabled, but i don't have 3d stuff (the visual effects). I try to enable the driver through

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`

sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko

when i put in the second command i get "insmod: error inserting '/lib/modules/2.6.24-23-generic/volatile/fglrx.ko': -1 Operation not permitted"

I had 3d working earlier but now i don't

i wanted to totally remove the drivers that i had previously installed and start over new with this same process

any ideas on what i can do?

---

