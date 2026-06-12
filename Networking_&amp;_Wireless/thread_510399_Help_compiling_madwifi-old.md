---
title: "Help compiling madwifi-old"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by trumps2k7 on 2007-07-26
Hi there!

I'm trying to compile madwifi-old (lastest version) for Ubuntu Feisty with but some errors arised. The reason why I'm trying to compile madwifi-old instead of using the supplied restricted-modules is that in dapper (but not in edgy or feisty) the signal strength for my Atheros AR5212 is much higher, same as in Window$, and Dapper uses madwifi-old I think.

So, I've first did untar the file "madwifi-old-current.tar.gz" into /usr/local/src/madwifi-old-r1417-20060128 , then did:"
  - check for dependencies (installed sharutils, linux-headers)

One question: the install.txt says it needs "kernel sources of running kernel", is linux-headers all I need?

  - sudo make (no ./configure available)
   And now the problem arises; I'm posting exactly as in terminal below:

> Checking if all requirements are met... ok.
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath; do \
                make -C $i || exit 1; \
        done
make[1]: Entering directory `/usr/local/src/madwifi-old-r1417-20060128/ath_hal'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/usr/local/src/madwifi-old-r1417-20060128/ath_hal MODVERDIR=/usr/local/src/madwifi-old-r1417-20060128/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/local/src/madwifi-old-r1417-20060128/ath_hal/ah_osdep.o
/usr/local/src/madwifi-old-r1417-20060128/ath_hal/ah_osdep.c:44:26: error: linux/config.h: No such file or directory
In file included from include/asm/system.h:4,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from include/linux/module.h:9,
                 from /usr/local/src/madwifi-old-r1417-20060128/ath_hal/ah_osdep.c:46:
include/linux/kernel.h:41:1: warning: "roundup" redefined
In file included from <command line>:1:
/usr/local/src/madwifi-old-r1417-20060128/ath_hal/../include/compat.h:46:1: warning: this is the location of the previous definition
make[3]: *** [/usr/local/src/madwifi-old-r1417-20060128/ath_hal/ah_osdep.o] Error 1
make[2]: *** [_module_/usr/local/src/madwifi-old-r1417-20060128/ath_hal] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/local/src/madwifi-old-r1417-20060128/ath_hal'
make: *** [all] Error 1



It seems it's not finding  some files, like config.h; I'll will need your help guys, since I'm new to linux :)

Any additional info will be happily supplied !

---

### Post by kevdog on 2007-07-26
Do you have an internet connection?? 

If you do, please type

sudo aptitude install linux-headers-`uname -r`

Then within the madwifi directory where you did the extraction of source files:
make clean
make

Seems like you are missing header files.  I tried what you did, and I didnt have any problems compiling with feisty.

---

### Post by trumps2k7 on 2007-07-27
Same problem :(

Maybe you have something installed other than linux-headers that I don't. The install.txt talks about  "kernel sources of running kernel", I don't know if that includes other things besides linux-headers.

Anyway, same errors still occurs.  :(

---

### Post by trumps2k7 on 2007-07-29
I still can't compile madwifi-old; :(

Any ideas??

---

