---
title: "Madwifi Compile Issues"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by chalkers on 2007-01-28
I am trying to install a wireless card with madwifi

After doing a make i get the following
```

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.19.1/build SUBDIRS=/root/madwifi-0.9.2.1 modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /root/madwifi-0.9.2.1/ath/ah_osdep.o
In file included from /root/madwifi-0.9.2.1/ath/ah_osdep.c:2:
/root/madwifi-0.9.2.1/ath/../hal/linux/ah_osdep.c:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/root/madwifi-0.9.2.1/ath/ah_osdep.o] Error 1
make[2]: *** [/root/madwifi-0.9.2.1/ath] Error 2
make[1]: *** [_module_/root/madwifi-0.9.2.1] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19'
make: *** [modules] Error 2

```

Does any one know how to fix it? (I am on Ubuntu 6.10 AMD 64)

Regards

Androo

---

