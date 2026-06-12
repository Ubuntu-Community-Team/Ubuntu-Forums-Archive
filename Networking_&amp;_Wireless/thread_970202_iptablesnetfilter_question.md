---
title: "iptables/netfilter question"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by arrowheart on 2008-11-04
Can I use netfilter or iptables to capture a packet which is wrapped
by a Ethernet frame with multicast mac address, but the destination IP
address (a unicast address) is not the local one? According to my
experiments, a local application can get such Ethernet frames by a raw
socket, but the payload, the IP packet with unmatched IP dest., cannot
be delivered to upper layers. Can iptables capture it and put it in
QUEUE?

Thanks

---

