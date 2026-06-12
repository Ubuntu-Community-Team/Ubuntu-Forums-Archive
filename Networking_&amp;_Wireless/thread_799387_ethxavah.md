---
title: "ethx:avah"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Lan on 2008-05-19
[size=1]

Wireless Problem:
When the Network Icon appears disconnected with little red [COLOR="Red"]x[/COLOR] and clicked. Error pop up: Contact your Network Administrator: Unable to locate device ehth3:avah in /proc/net/dev


[IFCONFIG]

eth3 and eth3:avah are identical. No idea, but maybe possible conflict.eth card, IRQ conflict?

eth2      Link encap:Ethernet  HWaddr 00:11:43:75:3C:1D
          inet6 addr: fe80::211:43ff:fe75:6f26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:896 (896.0 b)  TX bytes:492 (492.0 b)
          Interrupt:16 

eth3      Link encap:Ethernet  HWaddr _**00:12:F0:29:8A:9C**_
          inet6 addr: fe80::212:f0ff:fe29:786c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:15334 (14.9 KiB)  TX bytes:432 (432.0 b)
          Interrupt:18 Base address:0xa000 Memory:dfbff000-dfbfffff 



eth3:avah      Link encap:Ethernet  HWaddr _**00:12:F0:29:8A:9C**_
          inet6 addr: fe80::212:f0ff:fe29:786c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:15334 (14.9 KiB)  TX bytes:432 (432.0 b)
          Interrupt:18 Base address:0xa000 Memory:dfbff000-dfbfffff

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0

Some Commands:
lspci | grep Ethernet
dmesg | grep Ethernet

Corrected issue by editing /etc/iftab:

Input Info ie, mac address -

eth0 mac <mac address> arp 1
eth1 mac <mac address> arp 1
[color="blue"]added this line --> [/color][color="red"]eth3 mac <the mac the wireless card> arp 1 [/color]

Thanks.[/size]

---

