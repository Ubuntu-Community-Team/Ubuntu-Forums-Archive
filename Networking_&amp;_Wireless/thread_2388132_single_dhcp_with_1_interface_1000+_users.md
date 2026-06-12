---
title: "single dhcp with 1 interface 1000+ users"
date: 2018-03-28
forum: Networking &amp; Wireless
---

### Post by andrebtt on 2018-03-28
Good day all,

So it is possible to setup one ubuntu box with dhcp for 1000+ clients on one interface ? if so how ?

---

### Post by TheFu on 2018-03-29
Yes, but you'll need a larger than normal subnet.  Clearly a /24 won't do it, since that is only 254 hosts. Looks like a /22 is the smallest size. Going larger wouldn't be an issue from the DHCP perspective, but always speech with your network admins about the pros/cons for having different sized subnets.  Larger subnets can cause all sorts of broadcast traffic that might not be good.  If your IT group can prevent all the broadcasts, I've seen /20 subnets used in large corporations successfully.  There are other complications, especially if Windows desktops are involved.

DHCP doesn't really tax any system, so it is just getting the right-sized subnet.

Google found this: [https://help.ubuntu.com/community/isc-dhcp-server](https://help.ubuntu.com/community/isc-dhcp-server)

---

