---
title: "DNS: Can resolve internet addresses but not LAN addresses (Edgy)"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by NickForrington on 2007-01-12
Hi,
I'm running edgy and am having trouble with DNS:

I can resolve names of machines on the internet, but not within my own LAN

e.g.

```
nick@nick:~$ host george
Host george not found: 3(NXDOMAIN)
nick@nick:~$ host www.google.com
www.google.com has address 64.233.183.103
www.google.com has address 64.233.183.103
www.google.com has address 64.233.183.103
```

My /etc/resolv.conf shows the following the IP of my router as well as two DNS ips from my isp.

Any ideas?

Thanks in advance
Nick

---

