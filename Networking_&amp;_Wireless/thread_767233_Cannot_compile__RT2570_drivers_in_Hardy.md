---
title: "Cannot compile  RT2570 drivers in Hardy"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Woggles on 2008-04-25
I just performed the upgrade to Hardy and now I'm having issues compiling the drivers for the RT2570.  The driver is [http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt2570-k2wrlz-1.6.1.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt2570-k2wrlz-1.6.1.tar.bz2).

When I attempt to compile, this is my output..

woggles@1337-M1210:~/rt2570-k2wrlz-1.6.1/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/woggles/rt2570-k2wrlz-1.6.1/Module/rtusb_main.o
/home/woggles/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c: In function ‘usb_rtusb_probe’:
/home/woggles/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:1964: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/woggles/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:1984: error: ‘struct net_device’ has no member named ‘weight’
/home/woggles/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:2015: error: too few arguments to function ‘first_net_device’
make[2]: *** [/home/woggles/rt2570-k2wrlz-1.6.1/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/home/woggles/rt2570-k2wrlz-1.6.1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
rt2570.ko failed to build!
make: *** [module] Error 1


Does anybody know how to resolve this issue?

Thanks.

---

