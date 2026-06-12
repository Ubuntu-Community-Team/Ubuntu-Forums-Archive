---
title: "eth0 the same as eth0:1 ?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by _Dan on 2009-02-17
Hi,

I've set vnstat up to monitor bandwidth on eth0.

But I also have an eth0:1, which is a second IP address my hosting provider gave me.

from ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:8c:97:c9
          inet addr:[removed]  Bcast:[removed] Mask:255.255.255.0
          inet6 addr: [removed] Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:749168763 errors:0 dropped:4156317069 overruns:0 frame:0
          TX packets:636456324 errors:0 dropped:92 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4022420439 (4.0 GB)  TX bytes:4244146533 (4.2 GB)
          Interrupt:220 Base address:0x6000

eth0:1    Link encap:Ethernet  HWaddr 00:1c:c0:8c:97:c9
          inet addr:[removed]  Bcast:[removed]  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:220 Base address:0x6000
```

So my question is, will vnstat also monitor eth0:1 ? Are they one and the same? Or do I need to set up vnstat to monitor both separately? (I want all bandwidth on both IPs monitored)

---

