---
title: "Multicast in interfaces"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by mchowdhu on 2006-09-29
Hi,

How can I disable the multicast in the interfaces.

Output of the ifconfig is shown below. It shows that multicast is running. 


eth0      Link encap:Ethernet  HWaddr 00:0A:E6:C6:07:85
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fec6:785/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4015093 (3.8 MiB)  TX bytes:1449812 (1.3 MiB)
          Interrupt:10 Base address:0xd400

---

### Post by iheartme on 2006-11-20
A bit late perhaps, but what I did was to create a file in */etc/network/if-pre-up.d* and put the following in it:

```

#!/bin/bash
ifconfig eth0 -multicast
```

Works lika charm.

---

