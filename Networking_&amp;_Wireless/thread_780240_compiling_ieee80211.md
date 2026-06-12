---
title: "compiling ieee80211"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by jamicque on 2008-05-03
Hi,
yesterday i've installed new ubuntu 8.04 and i wanted to upgrade the ieee80211 package,
so i've downloaded it and installed build-essential. 
During the compilation of ieee80211 i got an error i have never seen before:
```
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.24-16-generic for ieee80211 components...
make -C /lib/modules/2.6.24-16-generic/build M=/home/jamicque/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
/home/jamicque/ieee80211-1.2.18/Makefile:17: 
/home/jamicque/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/jamicque/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/jamicque/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/jamicque/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/jamicque/ieee80211-1.2.18/ieee80211_module.o
/home/jamicque/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/jamicque/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/jamicque/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/jamicque/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/jamicque/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/jamicque/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/jamicque/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/jamicque/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

```

please help :(

---

### Post by jamicque on 2008-05-03
i've also tried the make SHELL=/bin/bash command but the effect is the same...
:/

---

### Post by oettam on 2008-05-16
Hi! I'm new.

I'm (trying to use) using Ubuntu 8.04 with:
Linux matteo-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

I've tried to install new driver for my wireless card, starting from re-installing ieee80211 (ieee80211-1.2.18 ). And here I stop.

Someone have a solution??

Probably a kernel incompatibility??

Thanks a lot.

---

