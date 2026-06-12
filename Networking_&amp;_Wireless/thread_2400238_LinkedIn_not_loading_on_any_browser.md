---
title: "LinkedIn not loading on any browser"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by ancadumi on 2018-09-04
For a day now I am unable to load LinkedIn in Ubuntu 16.04. Neither Firefox, Chromium and Opera work. The website loads from the same network on my phone, so I don't think it's an ISP issue. I also didn't notice any issue with other websites.

When I ping it in the browser it seems to work:

```

ping www.linkedin.com
PING pop-efr5.www.linkedin.com (185.63.145.1) 56(84) bytes of data.
64 bytes from 185.63.145.1: icmp_seq=1 ttl=56 time=10.0 ms
64 bytes from 185.63.145.1: icmp_seq=2 ttl=56 time=10.0 ms
64 bytes from 185.63.145.1: icmp_seq=3 ttl=56 time=10.1 ms
64 bytes from 185.63.145.1: icmp_seq=4 ttl=56 time=10.0 ms
64 bytes from 185.63.145.1: icmp_seq=5 ttl=56 time=10.1 ms
^C
--- pop-efr5.www.linkedin.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 10.019/10.095/10.196/0.131 ms

```

Traceroute also seems to resolve properly:

```

traceroute -I www.linkedin.com
traceroute to www.linkedin.com (185.63.145.1), 30 hops max, 60 byte packets
 1  145.108.179.1 (145.108.179.1)  2.611 ms  2.596 ms  2.593 ms
 2  130.37.250.121 (130.37.250.121)  1.918 ms  2.028 ms  2.064 ms
 3  130.37.6.102 (130.37.6.102)  1.768 ms  1.765 ms  1.762 ms
 4  130.37.6.92 (130.37.6.92)  3.317 ms  3.316 ms  3.313 ms
 5  GE5-1-1.2090.JNR01.Asd002A.surf.net (145.145.20.57)  2.378 ms  2.376 ms  2.375 ms
 6  80.249.211.185 (80.249.211.185)  10.073 ms  10.022 ms  9.991 ms
 7  * * *
 8  185.63.145.1 (185.63.145.1)  9.534 ms  9.179 ms  9.165 ms

```

Other things I tried that didn't work:
[LIST]
[*]set MTU to 1360 
[*]disable IPv6 DNS in Firefox 
[*]setting DNSSEC to off in /etc/systemd/resolved.conf 
[/LIST]


Has anyone experienced anything similar?

---

### Post by dsstorefile1 on 2018-09-06
What kinds of error messages (if any) do you get when navigating to LinkedIn with a browser?

---

