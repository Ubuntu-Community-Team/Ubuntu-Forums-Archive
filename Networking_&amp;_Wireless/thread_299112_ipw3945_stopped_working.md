---
title: "ipw3945 stopped working"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by nibblesmx on 2006-11-13
Hi everyone.

My wireless card has always worked flawlessly in edgy (i have been using edgy since the day dapper was announced).

I recently installed beryl, and now my card is not working at all. I think i found the problem, but i just don't know how to fix it.

```
nibblesmx@Odin:/sbin$ sudo modprobe ipw3945
sh: /sbin/ipw3945d-2.6.17-10-generic: No such file or directory
FATAL: Error running install command for ipw3945
```

and yes, the file is not present in the sbin directory. Actually, the file doesn't exist in my computer!

```
nibblesmx@Odin:/sbin$ locate ipw3945
/etc/modprobe.d/ipw3945
/lib/firmware/2.6.17-10-generic/ipw3945.ucode
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/ipw3945
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/ipw3945/Kconfig
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/ipw3945/Makefile
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945/debug.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945/module.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945/monitor.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945/promiscuous.h
```

Can anyone help me? I really need my wireless card :(

Thanks in advance :D

---

### Post by emdeem on 2006-11-13
I have no idea how installing beryl could have deleted that file, but to reinstall, it's part of linux-restricted-modules.

---

### Post by nibblesmx on 2006-11-13
thanks man.

Apparently, if you remove nvidia-kernel-common, apt-get also removes linux-restricted-modules.

thanks again :D

---

