---
title: "I can't install rt2750 driver on Ubuntu 8.0.4 HELP !"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by gnome1919 on 2008-07-26
Hi ;
I've just installed Ubuntu 8.04 through VMWare 6.0.4 on Windows Vista to use Aircrack. i've downloaded my wlan adapter driver from Aircrack website. mine is Linksys WUSB54G Ver4.0 and the patched driver to work with Aircrack is "rt2570-k2wrlz-1.6.1". but i can't install it. here is the error :

/rt2570-k2wrlz-1.6.1/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/ghavaninis/rt2570-k2wrlz-1.6.1/Module/rtusb_main.o
/home/ghavaninis/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c: In function â€˜usb_rtusb_probeâ€™:
/home/ghavaninis/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:1964: error: implicit declaration of function â€˜SET_MODULE_OWNERâ€™
/home/ghavaninis/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:1984: error: â€˜struct net_deviceâ€™ has no member named â€˜weightâ€™
/home/ghavaninis/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:2015: error: too few arguments to function â€˜first_net_deviceâ€™
make[2]: *** [/home/ghavaninis/rt2570-k2wrlz-1.6.1/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/home/ghavaninis/rt2570-k2wrlz-1.6.1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
rt2570.ko failed to build!
make: *** [module] Error 1

Please Help me :( :confused: , 
**By the way i'm good on Windows but a complete beginner on Linux**
Thx for your cooperation.

---

