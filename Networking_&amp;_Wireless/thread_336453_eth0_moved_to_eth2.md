---
title: "eth0 moved to eth2"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by strattonbrazil on 2007-01-11
When I first installed Ubuntu, eth0 was the ethernet and eth1 was the wireless.  Now, however, eth2 is the ethernet, which eth1 is still the wireless.  I have been using just wireless, so I don't know how long this has been going on.  

The reason this matters is Matlab, which I need to authenticate looks at the Mac address on eth0 and only eth0.  

How can I move eth2 back to eth0?  

I have a Toshiba Tecra S2 with Ubuntu 6.06.  
Here is my /etc/network/interfaces file:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid stratton
wireless-key 042b17598259360fdbce8b5cb6

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by spd106 on 2007-01-11
Check the mac address with **ifconfig** (at a terminal), then edit the /etc/iftab file, look in **man iftab** for details.

---

### Post by strattonbrazil on 2007-01-11
How am I supposed to modify it?  /etc/iftab has eth0 listed, but doesn't come up when I use ifconfig

*** /etc/iftab ***
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0f:b0:59:2d:32 arp 1
eth1 mac 00:12:f0:48:54:fb arp 1

*** ifconfig ***
eth1      Link encap:Ethernet  HWaddr 00:12:F0:48:54:FB
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe48:54fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1117270 (1.0 MiB)  TX bytes:400397 (391.0 KiB)
          Interrupt:58 Base address:0xe000 Memory:b4006000-b4006fff

eth2      Link encap:Ethernet  HWaddr 00:0F:B0:67:E7:2D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5376 (5.2 KiB)  TX bytes:5376 (5.2 KiB)

---

### Post by spd106 on 2007-01-11
Put the mac address of the card you want to be eth0 in the corresponding line in the iftab file.
I.e. ```
*** /etc/iftab ***
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0F:B0:67:E7:2D arp 1
eth1 mac 00:12:f0:48:54:fb arp 1
 
```
The other mac address will probably be assigned eth2 if it ever re-appears

---

