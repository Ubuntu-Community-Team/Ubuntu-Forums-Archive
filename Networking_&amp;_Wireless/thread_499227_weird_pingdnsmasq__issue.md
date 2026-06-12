---
title: "weird ping/dnsmasq  issue"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by mrt on 2007-07-12
I have dnsmasq running on my lan on a pc named "server0".  It is resolving addresses just fine, however, to ping it I have to add a "." to the name:
```
mike@mike-desktop:~$ ping server0
ping: unknown host server0
mike@mike-desktop:~$ ping server0.
PING server0 (192.168.1.115) 56(84) bytes of data.
64 bytes from server0 (192.168.1.115): icmp_seq=1 ttl=64 time=0.107 ms

--- server0 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.107/0.107/0.107/0.000 ms
mike@mike-desktop:~$

```

Why is that?

---

### Post by mrt on 2007-07-12
I removed the line "search local" from resolv.conf on the the workstation, that appears to have done the trick.

---

