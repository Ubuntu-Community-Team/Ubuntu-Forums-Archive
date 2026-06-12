---
title: "accessing server"
date: 2015-06-19
forum: Networking &amp; Wireless
---

### Post by sublevel42 on 2015-06-19
I am new to Ubuntu so this is my experiment :p I have a mostly mac household. I have an unraid server that i have been accessing via my main computer. I would like to access it from my Ubuntu system as well. However when i try to connect i get an error.

Unhandled error message: Could not connect to 192.168.0.25: No route to host

I have not idea what i need to do. I can get to the Western Digital Worldbook on the network with no issue. I can the other mac that has shared resources.
I need some ideas as to what i need to do.

Thanks!

---

### Post by sandyd on 2015-06-20
Hi, could you post the output of the following commands?
```

ifconfig -a
route -n
```

---

### Post by sublevel42 on 2015-06-20
dylan@Sublevel4-Ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:98:0b:2d  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe98:b2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:787597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255541584 (255.5 MB)  TX bytes:26474217 (26.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:92779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17762509 (17.7 MB)  TX bytes:17762509 (17.7 MB)

dylan@Sublevel4-Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
dylan@Sublevel4-Ubuntu:~$

---

### Post by sandyd on 2015-06-21
Ok, so you should be able to reach the computer, your on the same subnet.

Does ```

arping -I eth0 192.168.0.25
``` output anything?

---

### Post by sublevel42 on 2015-06-22
from that i get
ARPING 192.168.0.25 from 192.168.0.16 eth0

---

### Post by sublevel42 on 2015-06-27
what do i do next?

---

