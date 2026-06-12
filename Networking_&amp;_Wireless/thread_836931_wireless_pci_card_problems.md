---
title: "wireless pci card problems"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by williamirvine67 on 2008-06-22
Hey.

ive just installed ubuntu 8.04 on my system. the problem is my wireless card (PCI) wont work. its an ASUS WL-138G V2. ive downloaded the (linux) Driver of the asus site, but i dont know how to install it.

and another problem is that i cant enable "visual effects" on my system. any one got any clues? my GPU is an NVIDIA 5600XT 128mb.

Thanks for your Help.

William

---

### Post by drifter129 on 2008-07-17
i have the same problem here with installing the linux drivers for the wl-138g v2 wireless card.
when i try to compile i get the following:

ed@ed-desktop:~/drivers/src/linuxsta/src/wl/linux$ make clean
rm -f *.ko *.o *.c .*.o.cmd .*.ko.cmd
ed@ed-desktop:~/drivers/src/linuxsta/src/wl/linux$ make
Linux Directory is /lib/modules/2.6.24-16-generic/build
Linux Kernel Versions is 2.6.24-16-generic
make -C /lib/modules/2.6.24-16-generic/build CROSS_COMPILE= M=/home/ed/drivers/src/linuxsta/src/wl/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/ed/drivers/src/linuxsta/src/wl/linux/wlc_led.o
In file included from /home/ed/drivers/src/linuxsta/src/wl/linux/wlc_led.c:17:
/home/ed/drivers/src/linuxsta/src/wl/linux/../../include/typedefs.h:166: error: conflicting types for ‘bool’
include/linux/types.h:33: error: previous declaration of ‘bool’ was here
In file included from /home/ed/drivers/src/linuxsta/src/wl/linux/../../include/linux_osl.h:21,
                 from /home/ed/drivers/src/linuxsta/src/wl/linux/../../include/osl.h:24,
                 from /home/ed/drivers/src/linuxsta/src/wl/linux/wlc_led.c:19:
/home/ed/drivers/src/linuxsta/src/wl/linux/../../include/linuxver.h:19:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/ed/drivers/src/linuxsta/src/wl/linux/wlc_led.o] Error 1
make[1]: *** [_module_/home/ed/drivers/src/linuxsta/src/wl/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2

---

