---
title: "iptables match per source ip"
date: 2017-06-05
forum: Networking &amp; Wireless
---

### Post by waranty92 on 2017-06-05
hi guys I need iptables rule that will match not all source ip addresses, but will match per source ip address. I mean something like this 
-A INPUT -m state --state RELATED,ESTABLISHED -m limit --limit 100/second --limit-burst 100 -j REJECT --reject-with tcp-reset
but this limit (100) must not be for everyone, it must be per source ip address. is this possible with iptables ?

---

