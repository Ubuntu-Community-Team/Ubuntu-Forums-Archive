---
title: "routing and forwarding problem"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by budi_wibowo on 2013-09-09
Hi 
i setup ubuntu as BGP Router with bird installed
topology looks like this 
client -->distribution-router---->core-router---->upstream 
i believe bird has no issue, the issue is on packet forwarding between interface on core-router. 
and from most of article i read it is solved by making masquerade, and i try and works also but it is ISP core router that shall not use masquerade/nat on core-router.
i have tried to enable forwarding trough sysctl and ufw but seems no luck. 
assigning static route on core-router also no luck 


here's the ping test from core-router 
root@core-ix:~# ping -I eth2 8.8.8.8
PING 8.8.8.8 (8.8.8.8) from xxx eth2: 56(84) bytes of data.
From xxx icmp_seq=1 Destination Host Unreachable
From xxx icmp_seq=2 Destination Host Unreachable
From xxx icmp_seq=3 Destination Host Unreachable
^C
--- 8.8.8.8 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5030ms
pipe 3
root@core-ix:~# ping -I eth3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) from yyy eth3: 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=53 time=51.6 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=53 time=51.7 ms
^C
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 51.674/51.704/51.734/0.030 ms

any suggestion or idea is highly appreciated 

regards

budi wibowo

---

### Post by s-bodet on 2013-09-15
Hi,

it's a straightforward topology, it should work.
You will need to masquerade if the upstream router has no entry for the eth2 subnet in its routing table.

Steve

---

