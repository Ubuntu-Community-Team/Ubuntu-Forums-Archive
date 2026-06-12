---
title: "dell 1405+ubuntu 7.04: how to remove the alternate driver"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by schakravarthi on 2007-06-06
I am trying to get my broadcom 1390 recognized on a dell 1405.
I have reinstalled Ubuntu twice as the FAQ said, 

I realise I cant remove the old driver. e.g i get

sudo ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

I tried some of the ways of removing the driver but to no avail. see below
sudo ndiswrapper -r bcm43xx
couldn't delete /etc/ndiswrapper/bcm43xx: No such file or directory
sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules


ndiswrapper -v 
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.46
vermagic:       2.6.20-15-generic SMP mod_unload 586

---

### Post by weblordpepe on 2007-06-06
Im not sure on the flags you have put after ndiswrapper there, but you can use:
lsmod
to see what modules are loaded. And:
rmmod xxxx
to remove xxxx module.

And:
modprobe xxxx 
to insert xxxx module with its dependencies. I use insmod as well but I hear thats naughty.

---

