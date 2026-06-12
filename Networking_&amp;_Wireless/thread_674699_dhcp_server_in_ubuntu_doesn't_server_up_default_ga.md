---
title: "dhcp server in ubuntu doesn't server up default gateway"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by dev.null on 2008-01-22
I've searched around for this solution, but I keep coming up with a bunch of complaints from ubuntu clients that can't get the default gateway, if this is already posted somewhere please just pass along the link. Thanks!

I've been running a FC3 server serving dhcp for several years. I recently installed ubuntu and wanted to replace the FC3 with it. I had to modify the dhcpd.conf file obviously but for some reason can't get it to dynamically set the default gateway on the clients. The clients use to pick up the default gateway, but now they don't from ubuntu.

Attached is my conf file. My objective is to setup two zones within one subnet, one zone for "static" dhcp clients and one zone for dynamic ones. The older dhcp server allowed this easily by putting two different "pools" in one subnet, the newer conf doesn't seem to allow that.

Any suggestions?

---

