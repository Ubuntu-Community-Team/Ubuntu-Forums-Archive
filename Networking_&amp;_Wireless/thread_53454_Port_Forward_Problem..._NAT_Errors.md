---
title: "Port Forward Problem... NAT Errors"
date: 2005-07-31
forum: Networking &amp; Wireless
---

### Post by ephman on 2005-07-31
hi,

i've been having a persistant problem with forwarding port 50060 for azureus.  i've 100% forwarded the port properly in my router, in winxp i get not NAT errors, yet using ubuntu i get NAT errors.  also in iptables it's allowing the port to be forwared:

ACCEPT     tcp  --  anywhere             192.168.0.99        tcp dpt:50060
ACCEPT     udp  --  anywhere             192.168.0.99        udp dpt:50060

any help would be great thanks,

ephman

---

### Post by ephman on 2005-07-31
fixed it.  although i forwarded the port in both the router and my iptables, i didn't allow the service in firestarter.  so i had to add a rule to allow the service to allow port 50060.

ephman

---

