---
title: "Slow download speeds"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Damakin on 2008-04-18
I have 7.10 x64 on my desktop and I'm getting extremely slow download speeds (30k to <1k) on all applications. However, upload speeds are fine and everything works fine when I boot up Vista. I have tried disabling IPv6 (and in firefox too) however there has been no improvement.

Here is the output for my network adapter using ifconfig:
```

eth0
	Link encap:Ethernet  HWaddr 00:30:BD:F2:17:A9
	inet addr:192.168.11.10  Bcast:192.168.11.255  Mask:255.255.255.0
	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	RX packets:197998 errors:0 dropped:4658 overruns:0 frame:0
	TX packets:129447 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:289468842 (276.0 MB)  TX bytes:8483309145 (7.9 GB)
	Interrupt:12

```

I would be very grateful if someone could help me complete my migration from Vista :)

---

### Post by Damakin on 2008-04-18
I have come across a guide which has previously helped with slow connections at [http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509) and I pasted the following into my /etc/sysctl.conf

```

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```

I then typed sudo sysctl -p to make the changes come into effect, but I have not noticed any difference and my download speeds are still going at a measly rate, even after a reboot.

---

