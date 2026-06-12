---
title: "Now on my 2nd Network Card - Why doesn't Synaptic see existing connection?"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by sipickles on 2007-11-09
Ok I am growing tired of this....


I had a wired network card with a RTL8139 chip - apparently, despite being one of the most common NIC chips in existence, their support on gutsy is intermittent. So I ebayed a 3Com 990-TX-97 NIC.

The good news is, I am online. At least, I am online through Firefox.

However, I can't connect through Synaptics to download updates and software. In fact, I can't connect through Pidgin IM either.

I told FF not to use IPv6 which my router hates. If I do ifconfig I get:

eth1      Link encap:Ethernet  HWaddr 00:01:03:D8:71:63  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3234795 (3.0 MB)  TX bytes:617930 (603.4 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


This seems to suggest IPv6 is OFF. I have disabled it in aliases, even blacklisted the mutha!

Where can I go from here?

Thank you for your help!

S

--------------------------------


Enabling IPv6 makes an Ipv6 address appear in ifconfig. I can browse internet in firefox since about:config >> disableIPv6 = true
Disabling makes IPv6 address disappear from ifconfig, but still not internet outside firefox 

please help....

---

### Post by sipickles on 2007-11-09
Update your routers firmware.

My Dlink DSL-G604T had firmware dated 20040818. When I flashed it with 20050815, it flew!

YEEEEEEESSSS!  :guitar:

---

