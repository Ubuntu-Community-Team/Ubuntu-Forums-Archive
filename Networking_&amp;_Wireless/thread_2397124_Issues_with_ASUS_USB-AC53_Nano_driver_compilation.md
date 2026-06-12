---
title: "Issues with ASUS USB-AC53 Nano driver compilation"
date: 2018-07-25
forum: Networking &amp; Wireless
---

### Post by xerxesbeat on 2018-07-25
```
xerxesbeat@hitachiin:~/Downloads/5.2.4_20170919$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-29-generic/build M=/home/xerxesbeat/Downloads/5.2.4_20170919  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-29-generic'
Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/xerxesbeat/Downloads/5.2.4_20170919/core/rtw_cmd.o
In file included from /home/xerxesbeat/Downloads/5.2.4_20170919/include/osdep_service.h:47:0,
                 from /home/xerxesbeat/Downloads/5.2.4_20170919/include/drv_types.h:27,
                 from /home/xerxesbeat/Downloads/5.2.4_20170919/core/rtw_cmd.c:17:
/home/xerxesbeat/Downloads/5.2.4_20170919/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
/home/xerxesbeat/Downloads/5.2.4_20170919/include/osdep_service_linux.h:282:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/home/xerxesbeat/Downloads/5.2.4_20170919/include/osdep_service_linux.h:283:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/xerxesbeat/Downloads/5.2.4_20170919/core/rtw_cmd.o' failed
make[2]: *** [/home/xerxesbeat/Downloads/5.2.4_20170919/core/rtw_cmd.o] Error 1
Makefile:1552: recipe for target '_module_/home/xerxesbeat/Downloads/5.2.4_20170919' failed
make[1]: *** [_module_/home/xerxesbeat/Downloads/5.2.4_20170919] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'
Makefile:1801: recipe for target 'modules' failed
make: *** [modules] Error 2



```

any ideas?

---

### Post by jeremy31 on 2018-07-25
I would see if [https://github.com/MeissnerEffect/rtl8822bu](https://github.com/MeissnerEffect/rtl8822bu) works

---

### Post by xerxesbeat on 2018-07-25
that it did.  Thanks 

!Solved

---

