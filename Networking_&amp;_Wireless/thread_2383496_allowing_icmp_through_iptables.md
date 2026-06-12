---
title: "allowing icmp through iptables"
date: 2018-01-25
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-01-25
I've added the following to my iptable rules:

```
iptables -I INPUT -p icmp --icmp-type 8 -s 192.168.1.0/24 -d 192.168.1.1 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -I OUTPUT -p icmp --icmp-type 0 -s 192.168.1.1 -d 192.168.1.0/24 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

When I try to ping it's ip (192.168.1.1), it fails, and I get no response.

---

### Post by sniper8752 on 2018-01-25
Forgot to add "NEW".

---

### Post by wildmanne39 on 2018-01-25
Looks like you still need help but you have the thread marked as solved, if you need help please mark the thread unsolved.

Thanks

---

