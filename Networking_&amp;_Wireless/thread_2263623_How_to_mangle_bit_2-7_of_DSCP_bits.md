---
title: "How to mangle bit 2-7 of DSCP bits"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by houmingc on 2015-02-02
From the link below, bit 2-7 is DSCP bits.
if i mangle the output packet, is the below command for bit 2?
[B]iptables -t mangle -A OUTPUT -p tcp --dport 80 -j  DSCP --set-dscp 1
[/B]
And the below is for bit 3 then?
**[FONT=Thread-0000119c-Id-0000001f]iptables -t mangle -A OUTPUT -p tcp --dport 80 -j  DSCP --set-dscp 1[/FONT]**
 

[http://bogpeople.com/networking/dscp.shtml](http://bogpeople.com/networking/dscp.shtml)

---

