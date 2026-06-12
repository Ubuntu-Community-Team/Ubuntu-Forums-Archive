---
title: "Trouble compiling driver TP-link WN823N Ubuntu 18.04"
date: 2018-11-09
forum: Networking &amp; Wireless
---

### Post by stevenh22 on 2018-11-09
When I try to install the driver for my wifi USB adapter, I get the following message after using the make command:

make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-38-generic/build M=/home/saule/Downloads/tplink  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-38-generic'
Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/saule/Downloads/tplink/core/rtw_cmd.o
In file included from /home/saule/Downloads/tplink/include/osdep_service.h:47:0,
                 from /home/saule/Downloads/tplink/include/drv_types.h:27,
                 from /home/saule/Downloads/tplink/core/rtw_cmd.c:17:
/home/saule/Downloads/tplink/include/osdep_service_linux.h: In function ‘_init_timer’:
/home/saule/Downloads/tplink/include/osdep_service_linux.h:299:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/home/saule/Downloads/tplink/include/osdep_service_linux.h:300:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/saule/Downloads/tplink/core/rtw_cmd.o' failed
make[2]: *** [/home/saule/Downloads/tplink/core/rtw_cmd.o] Error 1
Makefile:1551: recipe for target '_module_/home/saule/Downloads/tplink' failed
make[1]: *** [_module_/home/saule/Downloads/tplink] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-38-generic'
Makefile:1828: recipe for target 'modules' failed
make: *** [modules] Error 2

What should I do? Thank you in advance!

---

### Post by chili555 on 2018-11-09
> Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, [COLOR="#FF0000"]please install libelf-dev,[/COLOR] libelf-devel or elfutils-libelf-devel"That's where I'd start.```
sudo apt install libelf-dev
```What is the driver file you are trying to compile? Where did it come from? We'd like to compile it ourselves and follow along or else suggest a better driver.

Since we'd like to confirm that you are getting the right driver for your device, please run and post:```
lsusb
```

---

