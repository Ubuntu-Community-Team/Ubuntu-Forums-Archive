---
title: "Xterasys XN-2511B, fresh Ubuntu install"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by fackue on 2008-04-10
I'm currently trying to install the adm8211 driver for my Xterasys XN-2511B wireless card. After I downloaded adm8211-20060111.tar.gz I extracted it to my desktop and cd'd into that folder using the terminal. I installed build-essentials through the package manager and type sudo make-install in the termainl and I get the following error when I try to compile the driver:

```
make -C /lib/modules/2.6.22-14-generic/build M=/home/f4cku3/Desktop/adm8211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/f4cku3/Desktop/adm8211/adm8211_hw.o
/home/f4cku3/Desktop/adm8211/adm8211_hw.c:29:26: error: linux/config.h: No such file or directory
/home/f4cku3/Desktop/adm8211/adm8211_hw.c: In function ‘adm8211_rx_skb’:
/home/f4cku3/Desktop/adm8211/adm8211_hw.c:520: error: ‘struct sk_buff’ has no member named ‘mac’
/home/f4cku3/Desktop/adm8211/adm8211_hw.c: In function ‘adm8211_interrupt_rci’:
/home/f4cku3/Desktop/adm8211/adm8211_hw.c:738: error: ‘struct sk_buff’ has no member named ‘mac’
/home/f4cku3/Desktop/adm8211/adm8211_hw.c: In function ‘adm8211_open’:
/home/f4cku3/Desktop/adm8211/adm8211_hw.c:2053: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/home/f4cku3/Desktop/adm8211/adm8211_hw.c:2053: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/f4cku3/Desktop/adm8211/adm8211_hw.c: In function ‘adm8211_80211_header_parse’:
/home/f4cku3/Desktop/adm8211/adm8211_hw.c:2396: error: ‘struct sk_buff’ has no member named ‘mac’
/home/f4cku3/Desktop/adm8211/adm8211_hw.c:2396: error: ‘struct sk_buff’ has no member named ‘mac’
make[2]: *** [/home/f4cku3/Desktop/adm8211/adm8211_hw.o] Error 1
make[1]: *** [_module_/home/f4cku3/Desktop/adm8211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
```

Similar to the errors [this guy is getting](http://ubuntuforums.org/showthread.php?t=651304&highlight=adm8211).

```
  *-network:0 UNCLAIMED   
       description: Network controller
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=128 mingnt=64
  *-network:1
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: eth0
       version: 10
       serial: 00:40:05:37:38:76
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

---

### Post by dstew on 2008-04-11
Besides build-essential, did you install the kernel-headers package for your kernel? Seems like your header files are missing. You can install kernel-headers using synaptic. Make sure to chose the one that matches the kernel you are using. Check the kernel version with```
uname -r
```

---

