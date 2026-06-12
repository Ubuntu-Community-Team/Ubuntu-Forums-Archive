---
title: "unable to provide services using 3G-dongle"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by ice-simx on 2015-09-26
when connect to internet using 3G-dongle and start ssh service,
unable to connect. to the system from the other system (ssh client)

ifconfig doesn't show the public ip address

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c6ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42071813 (42.0 MB)  TX bytes:5077503 (5.0 MB)

using google, can get the public ip address, but fails to login using ssh client :(

---

### Post by TheFu on 2015-09-26
I don't know of any cellular data providers who will allow inbound services. What is the WAN IP? If it isn't controlled by equipment you control, then opening any port for the desired inbound connection won't be possible. Sorry.

---

