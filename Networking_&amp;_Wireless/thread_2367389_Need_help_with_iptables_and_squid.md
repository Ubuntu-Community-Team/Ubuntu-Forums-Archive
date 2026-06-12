---
title: "Need help with iptables and squid"
date: 2017-07-29
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2017-07-29
installed squid have 
http_port 3128 transparent
always_direct allow all

have ip tables set with
iptables -t nat -A PREROUTING -i wlp2s0 -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -i wlp2s0 -p tcp --dport 443 -j REDIRECT --to-port 3128

I must be missing something I get not internet just times out host unreachable.

this is for a laptop need squid for content filtering. do not want child user to be able to turn it off.

---

