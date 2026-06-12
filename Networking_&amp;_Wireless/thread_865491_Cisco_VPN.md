---
title: "Cisco VPN"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by guber112 on 2008-07-20
Hello,
I'm trying to install a vpn from my university. And I'm getting the following error ```
Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/than/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/than/Desktop/vpnclient/linuxcniapi.o
In file included from /home/than/Desktop/vpnclient/Cniapi.h:15,
                 from /home/than/Desktop/vpnclient/linuxcniapi.c:31:
/home/than/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/than/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/than/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```
Any suggestion what this could be? Thank you.

---

### Post by casevh on 2008-07-20
Try following the instructions at:

[http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/](http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/)

They worked for me.

casevh

---

### Post by guber112 on 2008-07-20
> **casevh said:**
> Try following the instructions at:

[http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/](http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/)

They worked for me.

casevh


Thank you! That worked.

-Than

---

