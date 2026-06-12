---
title: "iptables - &quot;unknown arg&quot; --dport"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by Crowhurst01 on 2006-10-15
I am getting the "unknown arg" result when i try this code:

[COLOR="Red"]iptables -t nat -A PREROUTING -p udp --dport 5060 -i eth0 -j DNAT --to-destination 172.16.13.197[/COLOR]

I have researched and tried many variants, spellings and tried the full name --destination-port, for example.

I upgraded to ver. 1.3.6 of iptables and still no luck. I have even tried running known good lines from other users and still get the error

[COLOR="Red"]iptables v1.3.6: Unknown arg `--dport'[/COLOR]

Optimally i would like to match an incoming packet to eth0 based on its being UDP and the port, then i want to port forward it to   a destination inside the lan.

Any help is greatly appreciated.

---

