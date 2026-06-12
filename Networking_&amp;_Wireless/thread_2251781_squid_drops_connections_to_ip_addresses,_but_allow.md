---
title: "squid drops connections to ip addresses, but allows connections to domain names"
date: 2014-11-06
forum: Networking &amp; Wireless
---

### Post by igoryonya2 on 2014-11-06
when some program tries to connect to some address by using ip instead of a domain name, it gives me this in the log file:

```
1414709903.045      0 192.168.0.82 TCP_MISS/500 4429 GET http://213.59.3.178/xmlzone/release/1000/windows/versions.xml - HIER_NONE/- text/html "-"
1414709927.237      0 192.168.0.144 TCP_MISS/500 4565 GET http://192.168.24.1:2869/upnphost/udhisapi.dll? - HIER_NONE/- text/html "-"

```
When it connects by using a domain name, everything is working fine. When I get HIER_NONE, it doesn't even try to download anything, just drops. How can I solve this problem.

---

