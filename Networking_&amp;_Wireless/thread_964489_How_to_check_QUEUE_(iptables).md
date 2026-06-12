---
title: "How to check QUEUE (iptables)?"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by arrowheart on 2008-10-30
I use iptables to filter incoming packets with some particular protocols, such as ICMP, and the target is QUEUE.

=============================

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
QUEUE      icmp --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       

============================

How can I check the packets are filtered and put in the QUEUE?

Thanks

---

