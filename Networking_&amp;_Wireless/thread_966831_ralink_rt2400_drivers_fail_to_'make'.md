---
title: "ralink rt2400 drivers fail to 'make'"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by taels on 2008-11-01
according to [this guide]("http://http://www.methods.co.nz/doc/ralink-2400.html"), there are [open-source drivers]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") for the rt2400 wireless pci card. I followed the instructions in said guide up to the part where you run 'make' in the driver's Modules directory. Make returns these errors.

```

taels@flying-battery:~/wireless_driver/rt2400-1.2.2-b3/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.o
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:55: error: expected ‘)’ before string constant
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:59: error: expected ‘)’ before string constant
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c: In function ‘RT2400_probe’:
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:107: warning: format not a string literal and no format arguments
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:119: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:170: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:190: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘resource_size_t’
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c: In function ‘RT2400_open’:
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:238: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:238: error: (Each undeclared identifier is reported only once
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:238: error: for each function it appears in.)
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:238: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c: In function ‘rt2400_init_module’:
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:771: error: implicit declaration of function ‘pci_module_init’
make[2]: *** [/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/taels/wireless_driver/rt2400-1.2.2-b3/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rt2400.ko failed to build!
make: *** [module] Error 1

```

kinda like what happened to [this guy]("http://peb.pl/linux/247656-ubuntu-7-10-i-ralink-rt2400.html"), but... in english...
It looks like there's some kind of patch here, but I cant make any sense of it... How do I apply it?

---

### Post by taels on 2008-11-01
I pasted the appropriate section of that guys post into the /wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c file, then saved and ran make again, but that returned more errors than before...
 ```
taels@flying-battery:~/wireless_driver/rt2400-1.2.2-b3/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.o
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:55: error: expected ‘)’ before string constant
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:59: error: expected ‘)’ before string constant
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c: In function ‘RT2400_probe’:
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:107: warning: format not a string literal and no format arguments
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:119: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:170: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:190: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘resource_size_t’
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c: In function ‘RT2400_open’:
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:238: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:238: error: (Each undeclared identifier is reported only once
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:238: error: for each function it appears in.)
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:238: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c: In function ‘rt2400_init_module’:
/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.c:771: error: implicit declaration of function ‘pci_module_init’
make[2]: *** [/home/taels/wireless_driver/rt2400-1.2.2-b3/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/taels/wireless_driver/rt2400-1.2.2-b3/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rt2400.ko failed to build!
make: *** [module] Error 1

```

Anyone have an idea as to how to get the ralink rt2400 card to work?

---

