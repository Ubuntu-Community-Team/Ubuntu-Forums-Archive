---
title: "help with firehol"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by tx-uturn on 2008-06-05
My Ubuntu box gets to the internet just fine, but my XP box does not. The XP box has a default gateway of the Ubuntu box and both can ping each other just fine. Here is my firehol.conf file

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "nobody root"

# Accept all client traffic on any interface
interface eth0 inside
policy accept
protection strong
client all accept

interface eth1 outside
client all accept

router out inface eth0 outface eth1
route all accept
masquerade

I am running dansguardian and it works just fine on the Ubuntu box.

---

### Post by tx-uturn on 2008-06-06
OK, it's fixed.   I didn't RTFM.  

/etc/default/firehol   start firehol = YES

---

