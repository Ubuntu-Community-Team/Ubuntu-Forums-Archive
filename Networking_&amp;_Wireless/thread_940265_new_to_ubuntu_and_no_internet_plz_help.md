---
title: "new to ubuntu and no internet plz help"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by Dragon mystique on 2008-10-06
Hi, i just installed ubuntu on my Windows XP and my internet just wont works. I tryed what i got to understand in this furom but i got nothing more. 

I have Nvidia Nforce4 internet chipset on a motherboard Asus A8N-E

Here the result of the test if start for you to help me.

**ifconfig** :
eth0      Link encap:Ethernet  HWaddr 00:11:d8:c1:06:65   
          inet addr:10.0.11.134  Bcast:255.255.255.255  Mask:255.255.255.0 
          inet6 addr: fe80::211:d8ff:fec1:665/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:31668 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:1953336 (1.8 MB)  TX bytes:31960 (31.2 KB) 
          Interrupt:21 Base address:0xa000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:3543 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3543 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:0  
          RX bytes:226068 (220.7 KB)  TX bytes:226068 (220.7 KB) 

**route :**
Kernel IP routing table 
Destination Gateway  Genmask     Flags Metric Ref    Use Iface 
10.0.11.0      *   255.255.255.0   U    0     0      0  eth0 

**cat /etc/network/interfaces :**auto lo 
iface lo inet loopback 
iface eth0 inet dhcp 
auto eth0 

plz give me complete and clear instruction because im new to ubuntu and i dont perfectly understand english (i'm french)
I want to switch to linux but without internet noway

Plz help
and
Tanks

---

### Post by seagullplayer77 on 2008-10-06
Try going into a terminal and running

```
sudo dhconfig
```

and post the output of that.

Another question: Are you using a wired or a wireless connection?

EDIT: Never mind that second question...the tags answer it.

---

### Post by Dragon mystique on 2008-10-07
Here the result of your command

sudo: dhconfig: command not found 

i seached forum for similar command and i found sudo dhclient so i tried it and here is the result

sudo dhclient 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:11:d8:c1:06:65 
Sending on   LPF/eth0/00:11:d8:c1:06:65 
Sending on   Socket/fallback 
DHCPREQUEST of 10.0.11.134 on eth0 to 255.255.255.255 port 67 
DHCPACK of 10.0.11.134 from 10.0.1.1 
bound to 10.0.11.134 -- renewal in 265371 seconds. 

I have wired connection, no router, cable internet.

---

