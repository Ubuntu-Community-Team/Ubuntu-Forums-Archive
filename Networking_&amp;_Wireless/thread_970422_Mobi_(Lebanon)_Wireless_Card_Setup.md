---
title: "Mobi (Lebanon) Wireless Card Setup"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by woody22075 on 2008-11-04
I have just installed Ubuntu 8.10 on my HP 6715b.  I live in Lebanon and have a PCMCIA broadband wireless card (Mobi) using Lynx as the ISP.  How do I configure it?

Thanks for the assistance!

M

---

### Post by charbel_sara on 2009-02-10
hi
i have the same issue. any help plz
i have the drivers files
when i make this command : $ make
i got the following error

laptop:/tmp/mobi$ make
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/tmp/mobi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/mobi/ib-net.o
/tmp/mobi/ib-net.c: In function ‘ib_net_setup’:
/tmp/mobi/ib-net.c:303: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/tmp/mobi/ib-net.c:311: error: implicit declaration of function ‘SET_MODULE_OWNER’
/tmp/mobi/ib-net.c:342:50: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/tmp/mobi/ib-net.c: In function ‘ib_net_register’:
/tmp/mobi/ib-net.c:342: error: ‘INIT_WORK’ undeclared (first use in this function)
/tmp/mobi/ib-net.c:342: error: (Each undeclared identifier is reported only once
/tmp/mobi/ib-net.c:342: error: for each function it appears in.)
make[2]: *** [/tmp/mobi/ib-net.o] Error 1
make[1]: *** [_module_/tmp/mobi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

any help plz

---

