---
title: "(SMC 2862W) Prism54 softmac Compile Error"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by johnnywellas on 2007-12-11
Greetings!

I created this thread because i couldn't find any info on how to overcome this difficulty.

I am a Ubuntu noob using 2.6.22-14-rt Kernel (Ubuntu Studio dist.), and I'm having trouble compiling the Prism54 softmac drivers (I'm following [[COLOR="Red"]these instructions[/COLOR]]("http://jbnote.free.fr/prism54usb/index.html")).
So, according to the [[COLOR="Red"]SMC WLAN Chipset Overview[/COLOR]]("http://www.smcnetworks.cz/data/downloads/Katalogy/Catalogues/WLAN%20Chipset.pdf"), and given that I'm using a SMC2862W-G V.2 (product code 99-012084-312), my chipset should be a Conexant Cohiba GW3887IK.

As the [[COLOR="Red"]supported device list goes[/COLOR]]("http://prism54.org/newdrivers.html"), it should work ok with these drivers.

I copied the 2.5.8.0 firmware to the /lib/firmware/2.6.22-14-rt/isl3887usb_bare path (it should be at /usr/lib/hotplug/firmware/isl3887usb_bare, but there wasn't such a path anywhere), downloaded the latest islsm-workbench tarball, and did all these steps:
```
~$ tla register-archive jean-baptiste.note@m4x.org--libre http://jbnote.free.fr/\{archives\}/libre
~$ tla get jean-baptiste.note@m4x.org--libre/prism54-project--mainline prism54-project
~$ cd prism54-project
~$ make tla-import
~$ make load
```

I suppose everything went ok, except for the last part (make load), which returns the following errors:
```

wellas@whoami:~/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project$ sudo make load
test ! -d src/madwifi-bsd/net80211 || \
        make -C src/madwifi-bsd/net80211
make[1]: Entering directory `/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211'
make -C /usr/src/linux-headers-2.6.22-14-rt SUBDIRS=/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211 MODVERDIR=/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211/../symbols  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-rt'
  CC [M]  /home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211/if_media.o
In file included from include/linux/compiler-gcc4.h:4,
                 from include/linux/compiler.h:40,
                 from include/asm-generic/page.h:7,
                 from include/asm/page.h:201,
                 from /home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211/../include/compat.h:71,
                 from <command line>:1:
include/linux/compiler-gcc.h:33:1: warning: "__packed" redefined
In file included from <command line>:1:
/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211/../include/compat.h:55:1: warning: this is the location of the previous definition
/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211/if_media.c:54:26: error: linux/config.h: No such file or directory
In file included from include/linux/cpumask.h:84,
                 from include/asm/paravirt.h:18,
                 from include/asm/msr.h:78,
                 from include/asm/processor.h:17,
                 from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:85,
                 from include/linux/module.h:9,
                 from /home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211/if_media.c:56:
include/linux/kernel.h:42:1: warning: "roundup" redefined
In file included from <command line>:1:
/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211/../include/compat.h:46:1: warning: this is the location of the previous definition
make[3]: *** [/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211/if_media.o] Error 1
make[2]: *** [_module_/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/wellas/Desktop/Linux/Wifi/Prism54/islsm-workbench-latest/prism54-project/src/madwifi-bsd/net80211'
make: *** [madwifi] Error 2

```

So, from all the information I could have acess to (and barely understood...) i suppose that some of the scripts may not work very well with recent kernels.
I'd appreciate any help onto solving this issue. Either that or other way to be able to use the wifi receiver (maybe ndis wrapping the windows drivers), because I'm currently forced to use my old man's laptop to share the network with this pc via ethernet cable.

I chose to try and use this driver so that i could try to use the receiver in monitor mode :biggrin:, but it isn't really an obligation. I just need to be able to connect to my AP on the floor below.


Thank you very much!
Best Regards,

 Wellas

---

### Post by johnnywellas on 2007-12-12
Ok, i used ndiswrapper to compile a working driver, and it works (I'm using it as i write this post). Too bad for the monitor mode thingy, i guess that acquiring an atheros chipset adapter will be something to think about in the near future. Maybe I'll wait for the 802.11n draft to become final.

Good Ubuntuing!

Wellas

---

