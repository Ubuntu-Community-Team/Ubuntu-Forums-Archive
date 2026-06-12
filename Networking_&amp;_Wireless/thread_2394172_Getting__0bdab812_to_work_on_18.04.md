---
title: "Getting  0bda:b812 to work on 18.04"
date: 2018-06-13
forum: Networking &amp; Wireless
---

### Post by design+playbox on 2018-06-13
Hi all, 

I tried following the directions here: [https://ubuntuforums.org/showthread.php?t=2378892](https://ubuntuforums.org/showthread.php?t=2378892), however, this gave me a ton of compile errors.

```
chris@chris-development:~/rtl8822bu$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-23-generic/build M=/home/chris/rtl8822bu modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-23-generic'
  CC [M]  /home/chris/rtl8822bu/core/rtw_cmd.o
In file included from /home/chris/rtl8822bu/include/osdep_service.h:41:0,
                 from /home/chris/rtl8822bu/include/drv_types.h:32,
                 from /home/chris/rtl8822bu/core/rtw_cmd.c:22:
/home/chris/rtl8822bu/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
/home/chris/rtl8822bu/include/osdep_service_linux.h:262:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/home/chris/rtl8822bu/include/osdep_service_linux.h:263:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/chris/rtl8822bu/core/rtw_cmd.o' failed
make[2]: *** [/home/chris/rtl8822bu/core/rtw_cmd.o] Error 1
Makefile:1552: recipe for target '_module_/home/chris/rtl8822bu' failed
make[1]: *** [_module_/home/chris/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-23-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2



```

By any chance does anyone have a patch for what's currently at: [COLOR=#000000][FONT=&amp]https://github.com/jeremyb31/rtl8822bu.git? Or perhaps another URL with better source code for the current version of Ubuntu?

[/FONT][/COLOR]```
uname -a
Linux chris-development 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

Thanks in advance for the help!

---

### Post by praseodym on 2018-06-13
[https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613](https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613)

Try this one

---

### Post by design+playbox on 2018-06-19
Thanks  		praseodym, sorry for taking so long to reply.

So my system now sees enp35s0 going by ifconfig, however when I try to set up a new WiFi connection, only the physical card is a choice.

Do I need to do something else?

output of ifconfig:
```

enp35s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether b0:6e:bf:3a:33:c3  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

