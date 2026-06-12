---
title: "Problem with pptpd"
date: 2016-01-22
forum: Networking &amp; Wireless
---

### Post by giuseppe25 on 2016-01-22
Hey, I'm a new user at Ubuntu community :D


Today I get a VPS from _Amazons EC2_ and I'm trying set a_ PPTPD server_, but when I try connect I get error 800 - 807

I already setup my firewall to accept _protocol 47_ and _1723 port_, and I disabled my firewall too...
Error print: [http://prntscr.com/9tm2cr](http://prntscr.com/9tm2cr)

Here's some files config.

PPTPD-OPTIONS
```

refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128


ms-dns 8.8.8.8
ms-dns 8.8.4.4


nodefaultroute
lock
nobsdcomp
novj
novjccomp
nologfd

```
--
--
PPTPD.CONF
```

option /etc/ppp/pptpd-options
logwtmp
localip 192.168.0.1                                           << *_I just uncommented this line_*
remoteip 192.168.0.234-238,192.168.0.245           << *_I just uncommented this line_*

```

--
--
SYSCTL.CONF
```

net.ipv4.ip_forward=1

```

I already used this rule: [I]iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
[/I]

So, can someone help me please?

---

### Post by giuseppe25 on 2016-01-23
Someone? pls help!

---

