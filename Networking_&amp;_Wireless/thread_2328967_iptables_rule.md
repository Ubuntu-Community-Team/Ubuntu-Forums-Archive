---
title: "iptables rule"
date: 2016-06-26
forum: Networking &amp; Wireless
---

### Post by preq on 2016-06-26
I need to write an iptables rule which should work this way:
***drop all DNS request NOT directed to 8.8.8.8***

In my opinion the rule should be like this:

*iptables -A OUTPUT -o eth0 -p udp --sport 53 ! -d 8.8.8.8 - J DROP*

Is the rule correct?

Thanks a lot
preq

---

