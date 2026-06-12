---
title: "All eth0 data goes through lo"
date: 2004-12-12
forum: Networking &amp; Wireless
---

### Post by john280z on 2004-12-12
Slow network speeds - I have done the FireFox ipv6 mods - here is output of ifconfig:

root@dell150gx:/etc/modutils # ifconfig
eth0   Link encap:Ethernet  HWaddr 00:04:5A:8D:1E:5C
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe8d:1e5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:4724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4102 dropped:0 overruns:0 carrier:8190
          collisions:0 txqueuelen:1000
          RX bytes:4687229 (4.4 MiB)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xec00

lo       Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10597910 (10.1 MiB)  TX bytes:10597910 (10.1 MiB)

Any ideas?
Thanks - john

---

