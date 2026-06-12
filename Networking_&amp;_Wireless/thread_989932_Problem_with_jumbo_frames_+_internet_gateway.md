---
title: "Problem with jumbo frames + internet gateway"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by madmat333 on 2008-11-22
Hi All

I'm having an issue were some web sites will not load when I have jumbo frames enabled. 

The ubuntu box has 100M ethernet interface connecting to the modem, and 1 gigabit NIC connecting to the LAN

By setting up a proxy the problem goes away, but that would be because the LAN clients are not actually connecting to the web sites, the proxy service is so the external connections are not traversing the jumbo enabled LAN. 

the pppoe setup wizard allows for a clamping of the 'MSS' to 1452 bytes - which I have tried already. 

Any ideas? 

Mat

---

### Post by madmat333 on 2008-11-22
Solution found: 

There is a bug report for the pppoeconf's MSS clamping iptables rule that the script creates that prevents the clamping from working with the larger frames. 

instead of the clamping that the script sets use the following: 

iptables -t mangle -o "$PPP_IFACE" --insert FORWARD 1 -p tcp \
--tcp-flags SYN,RST SYN -m tcpmss --mss 1400:65495 -j TCPMSS \
--clamp-mss-to-pmtu

Mat

---

