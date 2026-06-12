---
title: "Iptables rule"
date: 2020-03-11
forum: Networking &amp; Wireless
---

### Post by ondrousn on 2020-03-11
Hello, I am trying to get more into iptables.

I have a following rule: ```
-A INPUT -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT
```

Do I understand correctly, that this rule accepts all incoming packets, that are negation of (SYN=1; FIN, RST and ACK=0), hence meaning SYN = 0?

In my understanding that would mean I accept all packets that have not SYN set, such as data packets etc?

---

