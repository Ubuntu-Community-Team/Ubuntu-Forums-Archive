---
title: "Compaq W200 Orinoco compile error"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by sschuler on 2007-10-22
This is on fiesty. ANd yes, I am a noob ;-)

I get this message when I run make:

make -C /usr/src/linux-headers-2.6.20-15-generic M=/home/steve/usb KERNELRELEASE=2.6.20-15-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/steve/usb/orinoco.o
/home/steve/usb/orinoco.c: In function ‘orinoco_get_drvinfo’:
/home/steve/usb/orinoco.c:4287: error: ‘struct net_device’ has no member named ‘dev’
/home/steve/usb/orinoco.c:4288: error: ‘struct net_device’ has no member named ‘dev’
make[2]: *** [/home/steve/usb/orinoco.o] Error 1
make[1]: *** [_module_/home/steve/usb] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

---

