---
title: "cant get dyndns to get through router..."
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by s_raghu20 on 2007-07-01
Hi Guys..

I am fairly new to Ubuntu/Liinux. 

I have this D-Link router, which works as the DHCP server as well. On the Router config, I have enabled a backward translation for handling an apache server in my local network to be routed when there is a request for the given ip address.

the mechanism works just fine while I am running the apache on Windows XP (the other boot point of the same laptop). However, within Ubuntu, I fail to get this working.

When I ping my dynamic dns based domain name, it gives the right ip. but when I ask for a route, it just doesnt find anything.

a traceroute to google works fine. It shows hitting the router as the first point while going out. and then whatever comes across. But in case of my own dyn-domain, it just doesn't find anything...

Two outputs...

```

raghav@raghav-ubuntu:/media$ traceroute google.com
traceroute: Warning: google.com has multiple addresses; using 72.14.207.99
traceroute to google.com (72.14.207.99), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  0.365 ms  0.363 ms  0.302 ms
 2  10.221.64.1 (10.221.64.1)  6.867 ms ch-gva01a-ra1-ge-1-1-0.aorta.net (213.46.171.53)  11.182 ms  11.027 ms
 3  ch-gva01a-ra1-ge-1-1-0.aorta.net (213.46.171.53)  11.762 ms  11.355 ms  12.010 ms
...
...

raghav@raghav-ubuntu:/media$ traceroute raghu20.dyndns.org
traceroute to raghu20.dyndns.org (80.219.0.182), 30 hops max, 40 byte packets
 1  * * *
 2  * * *


```

As it shows, its able to get the right ip address, but somehow cant get on with more..

Help please

regards
raghav..

---

### Post by avik on 2007-07-01
Are you sure apache is running properly and you can reach it via localhost?  Sorry I can't be of more help, but right now, that seems like the only possible problem.

---

### Post by s_raghu20 on 2007-07-01
Yeah, apache is running just fine. :)

---

