---
title: "Ubuntu 12.04 keeps getting the wrong gateway irrespective of what I do"
date: 2014-10-27
forum: Networking &amp; Wireless
---

### Post by harisund on 2014-10-27
My Ubuntu 12.04 box connects via another machine on the network.

I want to force a gateway of, let's say, 173.20.1.222. However, irrespective of what I have tried it keeps getting a gateway of 173.20.11.222. Why?

I have tried the following -

Edit /etc/dhcp/dhclient.conf. I removed "routers" from the request line, and have added supersede routers 173.20.1.22.

Edit /etc/network/interfaces and added "gateway 173.20.1.222" after "auto eth0" and "iface eth0 inet dhcp"

Edit /etc/network/interfaces and added "post-up route add default via 173.20.1.222 dev eth0" at the end.

Nothing works. Every single time, the default gateway when I do route is "173.20.11.222". Why is this happening? What's making it get that address? Why can't I over ride it?

---

