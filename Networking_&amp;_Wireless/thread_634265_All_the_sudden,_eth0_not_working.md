---
title: "All the sudden, eth0 not working"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by jstableford on 2007-12-07
My network interface card is no longer working, and I cannot see any reason why. My wireless card is working fine, however I really want the speed of ethernet since I have some network drives.

This stopped working after a restart. Then, "wired network" is no longer available as a pulldown option. Here is what ifconfig says:

eth1      Link encap:Ethernet  HWaddr 00:11:50:18:D6:66  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe18:d666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1205 errors:0 dropped:89 overruns:0 frame:0
          TX packets:1287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:957563 (935.1 KB)  TX bytes:174198 (170.1 KB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5584 (5.4 KB)  TX bytes:5584 (5.4 KB)

________________________________________________________


As you can see, it's no longer there. I here's my /etc/network/interfaces:

root@caliban:/etc/network# cat interfaces 
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
_______________________________________________________

All the lights are on on both ends. Any suggestions?

Thanks,

J

---

