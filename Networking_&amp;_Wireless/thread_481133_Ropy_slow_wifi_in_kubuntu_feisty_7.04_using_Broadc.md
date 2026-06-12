---
title: "Ropy slow wifi in kubuntu feisty 7.04 using Broadcom Corporation BCM4310"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by slybob on 2007-06-22
Hi,

My wireless is very slow and tricky to get connected with Knetworkmanager.

I have seen suggestions to disable IPv6 in modprobe. How do I do this is ubuntu?

```
andrew@andrew-laptop:/etc/modprobe.d$ lspci | grep Broadcom
05:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

andrew@andrew-laptop:/etc/modprobe.d$ uname -a
Linux andrew-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

andrew@andrew-laptop:/etc/modprobe.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"NETGEAR"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:6C:69:C6:2C
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

I intalled the driver this way
[http://ubuntuforums.org/archive/index.php/t-434946.html](http://ubuntuforums.org/archive/index.php/t-434946.html)

---

