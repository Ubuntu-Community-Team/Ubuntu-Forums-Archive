---
title: "Ubuntu 15.04 won't connect to the Ethernet network (wired connection"
date: 2015-09-19
forum: Networking &amp; Wireless
---

### Post by Sean_Pisano on 2015-09-19
Ok I have Gigabyte 990fxa-ud3 motherboard with on-board lan.  No connection to the network. 
When that did not work I threw in a lan card and disabled my on-board lan.  No connection to the network.
Now I have both cards active.  No connection to the network.

```

ifconfig gives me the following:

eth0

Link encap:Ethernet HWaddr c8:3a:35:d8:ef:93
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

eth1
Link encap:Ethernet HWaddr fc:aa:14:9a:c9:f8
inet6 addr: fe80::feaa:14ff:fe9a:c9f8/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1 errors:0 dropped:0 overruns:0 frame:0
TX packets:1 errors:0 dropped:47 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:60 (60.0 B) TX bytes:90 (90.0 B)

lo
Link encap:Local Loopback
inet addr:127.0.01 Mask:255.0.0.0
inet6 addr: ;;1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:713 errors:0 dropped:0 overruns:0 frame:0
TX packets:713 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:61643 (61.1 KB) TX bytes:61643 (61.1 KB)


```

I am a newbie and I have tried many of the solutions on this forum and nothing has worked.

Thanks 
Sean

---

### Post by Sean_Pisano on 2015-09-19
Apparently this is a motherboard problem  I have found the solution's on this thread:

[http://www.tomshardware.com/answers/id-1934663/ubuntu-internet-working.html](http://www.tomshardware.com/answers/id-1934663/ubuntu-internet-working.html)

Which lead me to some solution on this thread:

[http://ubuntuforums.org/showthread.php?t=2111223&page=2](http://ubuntuforums.org/showthread.php?t=2111223&page=2)

My solution is not to have usb 3.0.

---

