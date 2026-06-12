---
title: "D-Link DWL-G510 Rev. C Problem"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by Octavian.C on 2007-06-21
Hi!
I recently installed Ubuntu 7.04 on one of my old computers. it had a D-Link DWL-G510 wireless card in it, and I am having some problems getting it set up. First of all, it wont let me choose to connect to my AP through WPA-PSK method. All it has is WEP. So I did some searching around, and saw a few topics on this.
The guide that I am running off is [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29)
As the card is a Rev.C and uses the RT61 chipset. However, I encountered a problem while compiling the driver.  I typed in make all and this is what I got.

```
root@ubuntubox:~/RT61_Linux_STA_Drv1.1.0.0/Module# make all
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/root/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /root/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/root/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/root/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/root/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/root/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/root/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/root/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2

```

Can anyone help?

---

