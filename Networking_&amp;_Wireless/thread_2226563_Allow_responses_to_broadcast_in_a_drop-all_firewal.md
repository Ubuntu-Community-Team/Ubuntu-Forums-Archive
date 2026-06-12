---
title: "Allow responses to broadcast in a drop-all firewall"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by GigabyteProduction on 2014-05-28
My input policy is to drop all traffic unless it's part of an established connection or related to one.

```
iptables -P INPUT DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

but if an application makes a broadcast, and something responds directly to the broadcast, the incoming packet is marked as forming a new connection (i tested this with rules such as ```
iptables -A INPUT -m state --state NEW -j LOG --log-prefix "NEW: "
``` for each of the different states and a response to a broadcast is being marked with "NEW: ")

How can i allow responses to broadcasts to enter without removing my policy of "only allow what i start"?

---

### Post by SeijiSensei on 2014-05-28
duplicate

---

### Post by SeijiSensei on 2014-05-28
Responses to broadcasts are going to come from a well-known source.  For instance, DHCP uses broadcasts to request an address, but the response will come from the DHCP server.  I suggest a judicious mix of accepted server IPs and ports is the best approach.  There is no equivalent to established traffic when you're dealing with broadcasts.

So few services rely on broadcasts that you should be able to define precisely which replies are allowed and from where they can legitimately originate.

---

### Post by GigabyteProduction on 2014-05-29
Thank you for the response. It really stinks that there's not a failsafe way to do this, though.

---

