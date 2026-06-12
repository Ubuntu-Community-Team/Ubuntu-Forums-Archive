---
title: "Forward traffic from Loopback to interface"
date: 2016-02-02
forum: Networking &amp; Wireless
---

### Post by oho27m on 2016-02-02
Hi, 
On my computer there are a two networks cards , one for receive TS stream (eth0) and second to transmit further (eth1). when i receive stream first I send him to loopback interface and then from loopback interface forward to second ( Double synchronization) but ther is no traffic on eth1.

I enable in sysctl.conf foerarding multicast.
net.ipv4.ip_forward=1



tcpdump -i lo

07:29:47.492784 IP localhost.55580 > localhost.5000: UDP, length 1316
07:29:47.493124 IP 10.10.10.21.39946 > 10.10.10.21.5001: UDP, length 1316
07:29:47.493137 IP 10.10.10.21 > 10.10.10.21: ICMP 10.10.10.21 udp port 5001 unreachable, length 556
07:29:47.494282 IP localhost.55580 > localhost.5000: UDP, length 1316
07:29:47.494630 IP 10.10.10.21.39946 > 10.10.10.21.5001: UDP, length 1316
07:29:47.494644 IP 10.10.10.21 > 10.10.10.21: ICMP 10.10.10.21 udp port 5001 unreachable, length 556
07:29:47.495782 IP localhost.55580 > localhost.5000: UDP, length 1316
07:29:47.496120 IP 10.10.10.21.39946 > 10.10.10.21.5001: UDP, length 1316
07:29:47.496130 IP 10.10.10.21 > 10.10.10.21: ICMP 10.10.10.21 udp port 5001 unreachable, length 556
07:29:47.497277 IP localhost.55580 > localhost.5000: UDP, length 1316
^C

---

### Post by KenSharp on 2016-02-02
How, exactly, are you doing that?

---

### Post by oho27m on 2016-02-02
I use astra for receive stream over http and forward to localhost .

---

