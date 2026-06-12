---
title: "LAN drops packets - Internet works fine"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by Efrafa on 2008-03-04
My setup:
[LIST]
[*]Ubuntu 7.10
[*]DI-524 (D-Link) wireless router
[/LIST]

If I ping something like [www.google.com](www.google.com), I have *no packet loss*.  If I ping my local linux box at 192.168.0.2, I lose long series of packets.  Here's an example, pinging from my laptop (running OS X) :

> MacBook:~ george$ ping UbuntuBox.local
PING ubuntubox.local (192.168.0.102): 56 data bytes
64 bytes from 192.168.0.102: icmp_seq=51 ttl=64 time=30.581 ms
64 bytes from 192.168.0.102: icmp_seq=52 ttl=64 time=7.998 ms
64 bytes from 192.168.0.102: icmp_seq=53 ttl=64 time=1.816 ms
64 bytes from 192.168.0.102: icmp_seq=54 ttl=64 time=12.248 ms
64 bytes from 192.168.0.102: icmp_seq=55 ttl=64 time=2.946 ms
64 bytes from 192.168.0.102: icmp_seq=56 ttl=64 time=21.944 ms
64 bytes from 192.168.0.102: icmp_seq=57 ttl=64 time=11.302 ms
64 bytes from 192.168.0.102: icmp_seq=58 ttl=64 time=5.653 ms
64 bytes from 192.168.0.102: icmp_seq=59 ttl=64 time=12.424 ms
64 bytes from 192.168.0.102: icmp_seq=60 ttl=64 time=13.653 ms
64 bytes from 192.168.0.102: icmp_seq=61 ttl=64 time=11.648 ms
64 bytes from 192.168.0.102: icmp_seq=62 ttl=64 time=16.672 ms
64 bytes from 192.168.0.102: icmp_seq=63 ttl=64 time=3.136 ms
64 bytes from 192.168.0.102: icmp_seq=64 ttl=64 time=24.301 ms
64 bytes from 192.168.0.102: icmp_seq=65 ttl=64 time=22.293 ms
64 bytes from 192.168.0.102: icmp_seq=66 ttl=64 time=10.333 ms
64 bytes from 192.168.0.102: icmp_seq=67 ttl=64 time=5.405 ms
64 bytes from 192.168.0.102: icmp_seq=68 ttl=64 time=10.793 ms
64 bytes from 192.168.0.102: icmp_seq=69 ttl=64 time=11.163 ms
64 bytes from 192.168.0.102: icmp_seq=70 ttl=64 time=21.494 ms
64 bytes from 192.168.0.102: icmp_seq=71 ttl=64 time=44.754 ms
64 bytes from 192.168.0.102: icmp_seq=72 ttl=64 time=1.331 ms
64 bytes from 192.168.0.102: icmp_seq=73 ttl=64 time=9.141 ms
64 bytes from 192.168.0.102: icmp_seq=74 ttl=64 time=32.417 ms
64 bytes from 192.168.0.102: icmp_seq=75 ttl=64 time=20.792 ms
64 bytes from 192.168.0.102: icmp_seq=76 ttl=64 time=21.475 ms
64 bytes from 192.168.0.102: icmp_seq=77 ttl=64 time=2.300 ms
64 bytes from 192.168.0.102: icmp_seq=163 ttl=64 time=7.210 ms
64 bytes from 192.168.0.102: icmp_seq=164 ttl=64 time=10.190 ms
64 bytes from 192.168.0.102: icmp_seq=165 ttl=64 time=1.668 ms
64 bytes from 192.168.0.102: icmp_seq=166 ttl=64 time=2.782 ms
64 bytes from 192.168.0.102: icmp_seq=167 ttl=64 time=23.642 ms
64 bytes from 192.168.0.102: icmp_seq=168 ttl=64 time=3.897 ms
64 bytes from 192.168.0.102: icmp_seq=169 ttl=64 time=25.244 ms
64 bytes from 192.168.0.102: icmp_seq=170 ttl=64 time=3.433 ms
64 bytes from 192.168.0.102: icmp_seq=171 ttl=64 time=8.509 ms
64 bytes from 192.168.0.102: icmp_seq=172 ttl=64 time=18.405 ms
64 bytes from 192.168.0.102: icmp_seq=173 ttl=64 time=4.849 ms
64 bytes from 192.168.0.102: icmp_seq=174 ttl=64 time=28.770 ms
64 bytes from 192.168.0.102: icmp_seq=175 ttl=64 time=14.626 ms
64 bytes from 192.168.0.102: icmp_seq=176 ttl=64 time=5.146 ms
64 bytes from 192.168.0.102: icmp_seq=177 ttl=64 time=3.871 ms
64 bytes from 192.168.0.102: icmp_seq=178 ttl=64 time=1.583 ms
64 bytes from 192.168.0.102: icmp_seq=179 ttl=64 time=2.704 ms
64 bytes from 192.168.0.102: icmp_seq=180 ttl=64 time=3.688 ms
^C
--- ubuntubox.local ping statistics ---
181 packets transmitted, 45 packets received, 75% packet loss
round-trip min/avg/max/stddev = 1.331/12.450/44.754/9.986 ms

I noticed this when using rsync, which is difficult in this condition.

I haven't found anyone else with this problem, and I've run out of ideas.  I'd appreciate any help.

---

### Post by netztier on 2008-03-05
> **Efrafa said:**
> 
If I ping something like [www.google.com](www.google.com), I have *no packet loss*.  If I ping my local linux box at 192.168.0.2, I lose long series of packets.  Here's an example, pinging from my laptop (running OS X) :

[..]

I noticed this when using rsync, which is difficult in this condition.

I haven't found anyone else with this problem, and I've run out of ideas.  I'd appreciate any help.

WLAN networks are very prone to packet loss, by the nature of their design.

Things get even worse when there is WLAN-to-WLAN traffic where each data packet must use the "medium" twice, once from Client A to the AccessPoint, once from the AccessPoint to Client B. This often leads to a race for capacity and a lot of packet loss.

Their lossy nature makes WLANs quite unsuitable for protocols like NFS (over UDP), where the loss of a single WLAN frame (up to 1500bytes) kills the entire NFS request (typically 8192bytes long) which must then be repeated. Under such circumstances, using a very small NFS rsize/wsize (i.e. 1024bytes) can improve performance a lot.

So if you want a WLAN to perform, you have to make sure that the traffic pattern is "transit" for the WLAN-AP (from it's WLAN side to the LAN side or vice versa). Traffic that must be "reflected" by the AP is going to be a lot slower. This is why I strongly suggest to always run (file)servers on the wired part of the LAN, or at least on different WLAN-APs.

regards

Marc

---

### Post by Efrafa on 2008-03-05
> **netztier said:**
> WLAN networks are very prone to packet loss, by the nature of their design.

Things get even worse when there is WLAN-to-WLAN traffic where each data packet must use the "medium" twice, once from Client A to the AccessPoint, once from the AccessPoint to Client B. This often leads to a race for capacity and a lot of packet loss.


The Ubuntu box is connected by cable to the wireless router.  I'm not sure if that makes a difference.

The other thing is that it doesn't matter whether I'm sending 56-byte pings at 1 second intervals or large files by rsync at 2 MB/s.  Either way the connection may work for a while (anywhere from 1 second to several minutes) and then stops working for anywhere from 30 seconds to a few minutes.  If capacity is the problem, shouldn't rsync perform worse than the ping?

Thanks.

---

### Post by netztier on 2008-03-05
> **Efrafa said:**
> The Ubuntu box is connected by cable to the wireless router.  I'm not sure if that makes a difference.


It certainly does make a difference. But for the sake of a test, why don't you connect all systems to the wired part of the LAN and try rsync there and see if you still have packet loss with ICMP? And while you're at it: also try **iPerf** (from the universe repos) to see how fast the systems can actually talk to each other.

> 
Either way the connection may work for a while (anywhere from 1 second to several minutes) and then stops working for anywhere from 30 seconds to a few minutes.  


Sounds like an "noisy" environment - try setting the WLAN AP to another channel.

regards

Marc

---

### Post by Efrafa on 2008-03-05
> **netztier said:**
> 
Sounds like an "noisy" environment - try setting the WLAN AP to another channel.


That did it!  I still don't understand why noise would be such a problem when I'm using the wireless router for the LAN but not when I'm using it for wireless internet access.  Thanks for your help, though.

---

