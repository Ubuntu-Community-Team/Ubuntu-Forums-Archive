---
title: "TCP / UDP stack"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by jimmyh1972 on 2013-12-16
Hi 

Does anyone knows if Ubuntu opens TCP & UDP stack as default when booting?
are they opening with init, after INIT, when the kernel is loading?
are TCP or UDP opens parallel / on the same process?

thanks ahead
Jimmi

---

### Post by ian-weisser on 2013-12-16
> **jimmyh1972 said:**
> if Ubuntu opens TCP & UDP stack as default when booting?
Yes...sort of. Ubuntu initializes network interfaces and connects to networks automatically, including at boot.
No...sort of. The stack is an application using a protocol over a port to exchange data across a connection over an interface. If no application is exchanging data, but the connection is still live, then there is no stack.

> **jimmyh1972 said:**
> are they opening with init, after INIT, when the kernel is loading?
Init triggers network device activity and can initiate network connections. See /etc/init/networking.conf

> **jimmyh1972 said:**
> are TCP or UDP opens parallel / on the same process?
Same...sort of. Perhaps not in the way you think. TCP and UDP are not physically separated ports - just numbers that the system uses to keep track of streams (TCP) and datagrams (UDP). The same networking software usually handles both readily.

---

