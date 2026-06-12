---
title: "Connectivity Problems"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by alphaborie on 2008-04-19
Hello, new Ubuntu user here.
I cannot connect to the internet in any form (wireless, wired). Any help would be appreciated.:)

Gutsy Gibbon 7.10
AMD 64 arch

**ifconfig**
```
eth0   Link encap:Ethernet  HWaddr 00:0F:B0:BD:6B:19 
	  inet6 addr: fe80::20f:b0ff:febd:6b19/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:186743 (182.3 KB)
          Interrupt:22 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22880 (22.3 KB)  TX bytes:22880 (22.3 KB)
```
[B]
iwconfig[/B]

```
lo         no wireless extensions.

eth0     no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
             Mode:Managed  Access Point: Invalid 
	     RTS thr:off Fragment thr:off
             Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Any help is so greatly appreciated, I feel like banging my head against a wall. Thanks!

---

### Post by alphaborie on 2008-04-19
Additionally.

The Wireless adapter is a BROADCOM BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
according to the device manager. Although IWCONFIG calls it the 4318.

and

The Ethernet adapter is a RTL-8139/8139C/8139C+


Thanks again.

---

