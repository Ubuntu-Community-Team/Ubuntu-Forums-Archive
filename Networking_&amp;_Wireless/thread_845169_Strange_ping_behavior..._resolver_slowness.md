---
title: "Strange ping behavior... resolver slowness?"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by yogensha on 2008-06-30
In short, pinging a host by name in a third level domain results in pings only being sent every 5 seconds.

For example, while trying to ping the host 'host.sub.example.org', given the following resolv.conf:
```
search example.org
nameserver 192.168.4.13
```
...issuing the command:
```
ping host.sub
```
...results in pings only being sent every 5 seconds.  The latency is as expected.  I verified with tcpdump that the echo request is only sent every 5 seconds.

If I add:
```
search sub.example.org
```
...to resolv.conf and
```
ping host
```
the same thing happens.

This seems to be specific to ping.  I can telnet or ssh to hosts in the domain by short name and things work as expected in firefox.

I tried playing with 'options ndots' in resolv.conf to no avail.

Ideas?

---

### Post by yogensha on 2008-12-30
Disabling mDNS (avanhi) fixed this problem.  Apparently the ping application calls the mDNS and since mDNS doesn't run on my network, ping times out before sending sending the request.

---

