---
title: "Networking (bridging) problem with Ubtuntu 8.10 and VirtualBox"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by chino_sti on 2008-11-10
Ok, not really sure what happened here exactly, but I certainly don't know how to resolve it.  Basically I have an installation of Ubuntu 8.10, I have installed VirtualBox 2.0.4.  I have created a Windows XP Guest environment, and I have configured it to have a host interface as opposed to using NAT.  I have to configure it this way so that I can join it to my corporate network seamlessly.  Now I initially set it up following the VirtualBox instructions to setup the bridge and the adapters, it was working perfectly fine last week when I left work.  However came into work today, booted up and the internet on the Host environment (Ubuntu 8.10) is not working.  Internal network is working fine, I can read my mail, RDC to servers, I can ping my default gateway, however as soon as I try to get outside the firewall it is being lost.  Oddly, my guest installation of windows XP is working perfectly fine (which is where I am posting from). 

I am very new to using linux, in fact this is my first installation.  I am not too familiar with its networking setup yet... I am sure there is something simple I am missing, but hopefully the community can help!  This is what my network configuration looks like at the moment... let me know if there is anything else that would help in troubleshooting the issue.

br0       Link encap:Ethernet  HWaddr 00:15:c5:37:db:50  
          inet addr:192.168.55.22  Bcast:192.168.55.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe37:db50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16046746 (16.0 MB)  TX bytes:3902144 (3.9 MB)

eth0      Link encap:Ethernet  HWaddr 00:15:c5:37:db:50  
          inet addr:192.168.55.22  Bcast:192.168.55.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe37:db50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77289767 (77.2 MB)  TX bytes:10006647 (10.0 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138028 (138.0 KB)  TX bytes:138028 (138.0 KB)

vbox0     Link encap:Ethernet  HWaddr 16:13:b6:0c:f2:02  
          inet6 addr: fe80::1413:b6ff:fe0c:f202/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71408 errors:0 dropped:468 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:5773212 (5.7 MB)  TX bytes:62590606 (62.5 MB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:9d:01:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-9D-01-1E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

