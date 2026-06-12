---
title: "disable local ipadress to the internet"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by RaZer0r on 2007-12-07
hi all,
I'm not new to networking but this request i've never had before, and google wasn't the way since i wouldn't know what search strings to put in.
Anyway, i'm asking all of you to find out what rule i should need.
My boss asked me to create a system to block all outgoing ethernet from some sprecific ip's at work.
i'm using arno's firewall for my eth0(public ip)
and the rule: "iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE" to NAT all boxes to the internet.
How should/could i block eg: 192.168.0.190 from the internet, yet still allow it on the lan?

Any help, or clues are apreciated.

---

### Post by kidders on 2007-12-09
Hi there,

Something along these lines ought to work ...

```
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.190 -j DROP
```

---

