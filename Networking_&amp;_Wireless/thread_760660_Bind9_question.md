---
title: "Bind9 question"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by Phulerock on 2008-04-20
I have just set up DNS server sucessfully, using bind9. But have some question about configuration files, I 'm still not understand some option and value:
1. Forward and reverse zone:
```
$TTL 3D
@       IN      SOA @   ns1.a.com.  (
                        200608051 ; Serial, todays date + todays serial
                        8H      ; Refresh
                        2H      ; Retry
                        4W      ; Expire
                        1D)     ; Minimum TTL
```

I don't understand how the $TTL 3D work ? and the line " Serial, todays date + todays serial". 
What is SOA value, I don't understand that official site say: "	identifies the start of a zone of authority", anyone explain this more detail ? 

2. Where can I find the clearly, detail document that explain about RRs (resource record, what is  PTR, CNAME, TXT, A .etc)
](*,) 
Thanks alot

---

### Post by Phulerock on 2008-04-20
still have question:
in named.conf:
named.conf: "recursion" option   # this option provide allow/reject rescursion serivce, but what is recursion service ?

---

