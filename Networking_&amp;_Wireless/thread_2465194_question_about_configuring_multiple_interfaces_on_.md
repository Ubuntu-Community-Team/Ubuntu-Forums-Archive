---
title: "question about configuring multiple interfaces on a host within the same ipv6 sub-net"
date: 2021-07-24
forum: Networking &amp; Wireless
---

### Post by huiwang7436 on 2021-07-24
Hi All

I have an host, it has multiple interfaces connecting to the same IPv6 sub-net. Different IPv6 addresses are statically assigned to these interfaces. All these interfaces are assigned with the same gateway address.

I'd like to config the routing policy so that:

    All packets with source IP address specified goes out via the interface where the source IP address was assigned to.
    When source IP address is not specified by application. (ex. connect() without binding to an ip address), different interfaces' IP address is picked (as source IP address) randomly (if the destination IP address is different).

How do I config routing policy to achieve these in such an environment.

Please let me know if there are more appropriate mail lists for my question.

Thanks,

Hui

---

