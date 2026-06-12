---
title: "Karma and madwifi-old"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by haxorthematrix on 2006-09-05
Hello Everyone.

I spent some time recently trying to get Karma ([http://www.theta44.org/karma/)](http://www.theta44.org/karma/)), a wireless security tool, to work under Dapper.  I ran into a ton of problems, as Karma requires patched madwifi-old to run.  After I finally got all of it figured out and how to make the kernel modules work, I figured that I wasn't going to be the only one in this predicament.  

I've documented my procedure, and I'd like to give it back to you all - the forums have been very helpful, so time for me to give back.

[http://www.pauldotcom.com/KarmaUbuntu.pdf](http://www.pauldotcom.com/KarmaUbuntu.pdf)

Please, any and all comments and suggestions are appreciated.

- Larry

---

### Post by katabatic on 2007-06-17
No worky in Feisty :(:(:(:(:(

```
dtg@dtg-laptop:~/madwifi$ make
Checking if all requirements are met... ok.
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath; do \
                make -C $i || exit 1; \
        done
make[1]: Entering directory `/home/dtg/madwifi/ath_hal'
cp ./../hal/linux/ah_osdep.c ah_osdep.c
uudecode ./../hal/public/i386-elf.hal.o.uu
cp ./../hal/public/i386-elf.opt_ah.h opt_ah.h
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/dtg/madwifi/ath_hal MODVERDIR=/home/dtg/mad
wifi/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/dtg/madwifi/ath_hal/ah_osdep.o
/home/dtg/madwifi/ath_hal/ah_osdep.c:44:26: error: linux/config.h: No such file or directory
In file included from include/asm/system.h:4,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from include/linux/module.h:9,
                 from /home/dtg/madwifi/ath_hal/ah_osdep.c:46:
include/linux/kernel.h:41:1: warning: "roundup" redefined
In file included from <command line>:1:
/home/dtg/madwifi/ath_hal/../include/compat.h:46:1: warning: this is the location of the previous definiti
on
make[3]: *** [/home/dtg/madwifi/ath_hal/ah_osdep.o] Error 1
make[2]: *** [_module_/home/dtg/madwifi/ath_hal] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dtg/madwifi/ath_hal'
make: *** [all] Error 1

```

---

