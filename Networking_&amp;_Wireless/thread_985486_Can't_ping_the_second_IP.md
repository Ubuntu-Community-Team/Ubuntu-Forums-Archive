---
title: "Can't ping the second IP"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by xzhou001@cs.fiu.edu on 2008-11-17
I installed Ubuntu server 8.0.4. Right now I just added the second network card to my server and got the correct IP from DHCP server. But I couldn't ping the IP.  The first one is still working perfectly. I can ping, ssh, and web access it.  Did I miss configuring something? Any help is highly appreciated!

---

### Post by Iowan on 2008-11-17
Post results of **ifconfig** and contents of /etc/network/interfaces.  You don't have both NIC's in the same subnet?

---

### Post by xzhou001@cs.fiu.edu on 2008-11-17
eth0      Link encap:Ethernet  HWaddr 00:e0:81:5f:bd:99  
          inet addr:131.94.14.xxx  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe5f:bd99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34415 (33.6 KB)  TX bytes:11007 (10.7 KB)
          Interrupt:22 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:e0:81:5f:bd:98  
          inet addr:131.94.13.xxx  Bcast:255.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::2e0:81ff:fe5f:bd98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10532 (10.2 KB)  TX bytes:3752 (3.6 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)


/etc/network/interfaces is as follows

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The second network interface
auto eth1
iface eth1 inet dhcp


We have hostname for each NIC. Before today we only registered the eth0 for testing one website. Now we need testing a different project at the same time. so we registered the second one. Both NICs are on the same server. Thank you!

---

