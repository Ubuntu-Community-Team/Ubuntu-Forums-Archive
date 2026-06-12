---
title: "update namecheap with DDNS"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2014-02-07
I'm using namecheap and it supports ddns I can update my @ from one box, but I can update a subdomain.

How do I configure the code to work on a subdomain

This works.

```

# /etc/ddclient.conf

protocol=namecheap
server=dynamicdns.park-your-domain.com
login=l...n.us
password=fxxx
@
daemon=3600

```


I tried this (supposedly) for a sub-domain from another machine

```



# /etc/ddclient.conf

protocol=namecheap
server=dynamicdns.park-your-domain.com
login=l...n.us
password=fxxx
subdomain
daemon=3600


```

---

