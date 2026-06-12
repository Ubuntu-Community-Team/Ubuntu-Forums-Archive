---
title: "to install a cisco vpn client"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by kungfu_panda on 2008-10-13
Hi guys,

i want to install a cisco vpn client(Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer) on my ubuntu, there is shell script that comes with the application, when i run it i have the output below, how should i fix that? 

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/fredb/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/fredb/Desktop/vpnclient/linuxcniapi.o
/home/fredb/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /home/fredb/Desktop/vpnclient/Cniapi.h:15,
                 from /home/fredb/Desktop/vpnclient/linuxcniapi.c:34:
/home/fredb/Desktop/vpnclient/GenDefs.h:114: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
/home/fredb/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/fredb/Desktop/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/fredb/Desktop/vpnclient/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’
/home/fredb/Desktop/vpnclient/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’
/home/fredb/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/fredb/Desktop/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/fredb/Desktop/vpnclient/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’
/home/fredb/Desktop/vpnclient/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’
/home/fredb/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’
/home/fredb/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/fredb/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/fredb/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
fredb@fredb-laptop:~/Desktop/vpnclient$

---

