---
title: "VPN client help"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by japtar10101 on 2007-12-19
Some of my college work requires accessing their vpn server, and fortunately, they have the installation tar.gz file and instructions to work with.  However, the installation fails for some reason, as follows:
```
Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/omiyat/Install/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/omiyat/Install/vpnclient/linuxcniapi.o
/home/omiyat/Install/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/omiyat/Install/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/omiyat/Install/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/omiyat/Install/vpnclient/linuxcniapi.c:322: error: ‘struct sk_buff’ has no member named ‘nh’
/home/omiyat/Install/vpnclient/linuxcniapi.c:323: error: ‘struct sk_buff’ has no member named ‘mac’
/home/omiyat/Install/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/omiyat/Install/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/omiyat/Install/vpnclient/linuxcniapi.c:436: error: ‘struct sk_buff’ has no member named ‘mac’
/home/omiyat/Install/vpnclient/linuxcniapi.c:437: error: ‘struct sk_buff’ has no member named ‘nh’
/home/omiyat/Install/vpnclient/linuxcniapi.c:440: error: ‘struct sk_buff’ has no member named ‘h’
/home/omiyat/Install/vpnclient/linuxcniapi.c:440: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/omiyat/Install/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/omiyat/Install/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```
What does these errors mean?  If it has to do with wireless, I have no plan to use one....

---

### Post by tjksn on 2007-12-19
Try using VPNC instead.  This is available through synaptic and installs rather easily.  I did have to do some additional install to get network manager to restart with VPNC, but on another it did that automatically.  Anyway, once you have it installed you left click on your network connection icon and the menu will show VPN connections with a configure option.  There you will enter the information needed such as the group name, user name, etc.  When you have it connect it will prompt for you user password and the group password.  If all is setup right it will connect.

Tom

---

### Post by timcredible on 2007-12-19
and, since your post sounds like it's a cisco vpn, cisco.com has their linux vpn software, in case you need a newer or older version.  i tested the cisco vpn client with their 3030 vpn concentrator a few years ago, it worked ok, i don't remember any problems, but i used a mepis machine for that test (back when mepis was .rpm based).

---

### Post by japtar10101 on 2007-12-19
> **tjksn said:**
> Try using VPNC instead.  This is available through synaptic and installs rather easily.  I did have to do some additional install to get network manager to restart with VPNC, but on another it did that automatically.  Anyway, once you have it installed you left click on your network connection icon and the menu will show VPN connections with a configure option.  There you will enter the information needed such as the group name, user name, etc.  When you have it connect it will prompt for you user password and the group password.  If all is setup right it will connect.

Tom

I've installed VPNC, but I can't find the icon you're telling me about.  When I run vpnc on the terminal, It asks me for the "IPSec gateway address", something that isn't provided in the school website.  I believe the package they gave out installed the settings for you, but unfortunately it's a Red Hat distribution, which may be the cause of the problem.

Anyway, my windows laptop should have the setting information.  where can I find the following information from it? :
```

Enter IPSec gateway address: 
Enter IPSec ID for : 
Enter IPSec secret for @:
```

---

