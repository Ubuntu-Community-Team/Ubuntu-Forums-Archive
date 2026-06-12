---
title: "DHCP3-Server"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by krj32 on 2007-04-25
I am using dhcp3-server but when it assigns ip addresses from my range to dynamic computers it starts assigning with the last address instead of the first.  For example, i have my range set at 192.168.0.2 through 192.168.0.99.  Right now there are only 2 other computers on the network and they get addresses 192.168.0.99 and 192.168.0.98.  Does anyone know how to solve this issue?  Thanks.

---

### Post by dreadlord_chris on 2007-04-25
> **krj32 said:**
> I am using dhcp3-server but when it assigns ip addresses from my range to dynamic computers it starts assigning with the last address instead of the first.  For example, i have my range set at 192.168.0.2 through 192.168.0.99.  Right now there are only 2 other computers on the network and they get addresses 192.168.0.99 and 192.168.0.98.  Does anyone know how to solve this issue?  Thanks.

Why is this an issue? It really doesn't matter where assignment starts, or that assignments are given out in any order. The only 2 important conditions are that: all IP's must be unique, and all assignments must be within the configured range.

---

