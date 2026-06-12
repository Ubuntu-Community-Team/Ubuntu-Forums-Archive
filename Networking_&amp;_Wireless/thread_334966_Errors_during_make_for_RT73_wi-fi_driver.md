---
title: "Errors during make for RT73 wi-fi driver"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by joemilx on 2007-01-09
Followed the procedure detailed in 
    "WifiDocs/Device/Belkin F5D7050 ver 3000 (Ralink rt73 driver)"
in the Community Documents section .

All went well until the make in step 5.  Then I got:

QUOTE:
joe@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/joe/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
In file included from /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:99,
                 from /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm-i386/atomic.h:17: error: conflicting types for ‘atomic_t’
include/asm/atomic.h:18: error: previous declaration of ‘atomic_t’ was here
include/asm-i386/atomic.h:46: error: conflicting types for ‘atomic_add’
include/asm/atomic.h:47: error: previous definition of ‘atomic_add’ was here
include/asm-i386/atomic.h:61: error: conflicting types for ‘atomic_sub’
include/asm/atomic.h:62: error: previous definition of ‘atomic_sub’ was here
include/asm-i386/atomic.h:78: error: conflicting types for ‘atomic_sub_and_test’
include/asm/atomic.h:79: error: previous definition of ‘atomic_sub_and_test’ was here
include/asm-i386/atomic.h:95: error: conflicting types for ‘atomic_inc’
include/asm/atomic.h:96: error: previous definition of ‘atomic_inc’ was here
include/asm-i386/atomic.h:109: error: conflicting types for ‘atomic_dec’
include/asm/atomic.h:110: error: previous definition of ‘atomic_dec’ was here
include/asm-i386/atomic.h:125: error: conflicting types for ‘atomic_dec_and_test’
include/asm/atomic.h:126: error: previous definition of ‘atomic_dec_and_test’ was here
include/asm-i386/atomic.h:144: error: conflicting types for ‘atomic_inc_and_test’
include/asm/atomic.h:145: error: previous definition of ‘atomic_inc_and_test’ was here
include/asm-i386/atomic.h:164: error: conflicting types for ‘atomic_add_negative’
include/asm/atomic.h:165: error: previous definition of ‘atomic_add_negative’ was here
include/asm-i386/atomic.h:182: error: conflicting types for ‘atomic_add_return’
include/asm/atomic.h:183: error: previous definition of ‘atomic_add_return’ was here
include/asm-i386/atomic.h:208: error: conflicting types for ‘atomic_sub_return’
include/asm/atomic.h:193: error: previous definition of ‘atomic_sub_return’ was here
In file included from /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:99,
                 from /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm-i386/atomic.h:248:1: warning: "atomic_set_mask" redefined
In file included from include/asm/spinlock.h:4,
                 from include/linux/spinlock.h:86,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:44,
                 from include/linux/module.h:9,
                 from /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:63,
                 from /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm/atomic.h:418:1: warning: this is the location of the previous definition
In file included from /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:184,
                 from /home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
/home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_def.h:814:49: warning: backslash and newline separated by space
/home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable ‘device’
make[2]: *** [/home/joe/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/joe/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
joe@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ 

I'm a relative newbie to Linux and would greatly appreciate your assistance to get through this.  Thus far I'm very impressed with Ubuntu 6.10 64-bit and the helpfulness of the Community.

My Config:

ASUS A8V-VM, Athlon 64 3200+, 2GB PC3200 RAM, 4x Seagate 160GB SATA-2 HDD, Zonet ZEW2500P wi-fi adapter(seen as Ralink 2570),  Edgy Eft 6.10 64-bit with all updates applied.

---

### Post by lenst on 2007-01-20
I had the same problem. I commented out the include of asm-i386 in rt_config.h:
//#include <asm-i386/atomic.h>        
And then it built, with warnings. The module does however not work. Installing the module gives kernel oops:

pentax kernel: [  674.261954] Oops: 0002 [1] SMP 
pentax kernel: [  674.262334] CR2: 0000000000094000

Also iwconfig just hangs.

---

### Post by TheCaptain2000 on 2007-02-03
follow the instructions you find at  [http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)
the howto is in Italian, don't yu mind that, just execute all those unix commands one after the other, I have the rt73 working with WPA on kubuntu 64
Ren

:guitar:

---

### Post by benson444 on 2007-02-03
Thanks Captain! I got my brother's belkin working using the same guide as joemilx but couldn't find anything about WPA.

Cheers! :-)

---

