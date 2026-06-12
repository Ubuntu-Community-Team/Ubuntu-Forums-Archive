---
title: "Really basic ubuntu network"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by khunphil on 2008-10-06
Hi,

I have 2 ubuntu Hardy Destop PC (A and B), on an Ethernet LAN, 2 IP 192.168.1.50 and 192.168.1.59, same workgroup, connected via a HUB ... but when I got to Places / Network, I cannot see each other !

I can ping A from B and B from A.

My IP gateway (not sure we need) is 192.168.1.1 (router for Internet).

I don't know what to do so I can see then in Network Place. Or maybe is it normal ? Any easy networking guide ? Any misconfiguration ? I begin to believe I missed something ...

Thanks,

Philippe

PC A :
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:ab:ae:4d  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:feab:ae4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1946842 (1.8 MB)  TX bytes:82481 (80.5 KB)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102600 (100.1 KB)  TX bytes:102600 (100.1 KB)

---

### Post by linux6994 on 2008-10-06
You will need a DNS and Gateway.  Usually the DNS and Gateway are the same on a small or home network. If you are behind a router then point both to that device. Each Ubuntu PC will need to have a directory shared so that it can be seen. Install system-config-samba and use system>admin>samba and add your Documents, writable, visible and set server settings to share.


In order to be seen you have to show something. 

Good Luck.

---

### Post by khunphil on 2008-10-06
Hi,

> **linux6994 said:**
> You will need a DNS and Gateway.  Usually the DNS and Gateway are the same on a small or home network. If you are behind a router then point both to that device.

That was done right.

> **linux6994 said:**
>  Each Ubuntu PC will need to have a directory shared so that it can be seen. Install system-config-samba and use system>admin>samba and add your Documents, writable, visible and set server settings to share.In order to be seen you have to show something. 

Well I didnt know that I needed Samba to do it with 2 Ubuntu PC, and needed to show something. I will give it a try.

Thanks for your quick answer.

Philippe

---

