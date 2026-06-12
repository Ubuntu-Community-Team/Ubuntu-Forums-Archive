---
title: "QinQ supported in Ubuntu 16.04 with 802.1q in both tags?"
date: 2017-08-16
forum: Networking &amp; Wireless
---

### Post by apoz on 2017-08-16
Hi all,

I'd just want to know  if Q-in-Q double vlan tagging in supported in kernel 4.4.0 _with both tags using 802.1q type of tag _(instead of using 802.1ad type in external tag) in IPv6 traffic.


I configure some veths to do such double tagging, and it apparently works, but for ICMPv6 encapsulated messages I get a "IPV6 header not found" line in syslog.

Thanks!

---

