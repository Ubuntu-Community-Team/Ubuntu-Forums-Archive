---
title: "Realtek rtl8192cu"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by XtbA3cC on 2013-10-20
Hi.
I have a problem. I've bought wireless usb rlt but i cannot install it.

```

hogan@ninety:/drivers/net/wireless/rtl8192cu$ sudo make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-29-generic/build M=/drivers/net/wireless/rtl8192cu  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
  CC [M]  /drivers/net/wireless/rtl8192cu/core/rtw_cmd.o
In file included from /drivers/net/wireless/rtl8192cu/core/rtw_cmd.c:24:0:
/drivers/net/wireless/rtl8192cu/include/osdep_service.h:49:29: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/drivers/net/wireless/rtl8192cu/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/drivers/net/wireless/rtl8192cu] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'
make: *** [modules] Error 2
hogan@ninety:/drivers/net/wireless/rtl8192cu$ sudo make install
install -p -m 644 8192cu.ko  /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/
install: cannot stat `8192cu.ko': No such file or directory
make: *** [install] Error 1



```

What i have to do?

---

### Post by varunendra on 2013-10-22
Looks like a dependency or compatibility problem. Where have you got the driver from?

And, although not related to above errors, are you sure it is correct driver for you (USB) device and you need it?

Please post back the output of -
```
lsusb
```
..while the usb adapter is plugged in, so we can see if you really need the proprietary driver for it, and the one you are trying is correct one.

---

