---
title: "Multiple interfaces, Setting Default outgoing traffic."
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by Jasn_Tiamak on 2008-08-27
Ok, Heh, I hope I can explain this clearly.

I have an Ubuntu server and two completely separate networks.  They both have their own gateways.  On my network I'm set static.  I just dropped in a second NIC and hooked up the other Network which is DHCP.  I have addresses from both networks.  Here's the tricky bit for me.  I would like the DHCP network to be able to access the data/services on the Server, but I do not want the server to use the DHCP network as outgoing to the internet.  When I check the public IP of the box right now it is the same as the DHCP network.  Is there a way to force all traffic to use the Static network's connection?

Sorry if this is garbled, having a caffeine crash atm.

Thanks,
Jasn

---

### Post by mips on 2008-08-27
This one is easy.

Make sure your default route (0.0.0.0) points to the static eth interface.

Configure a static route that only routes traffic to the dhcp network. ie if the the dhcp network uses 192.168.5.0 then specify 192.168.5.0 with a mask of 255.255.255.0 for the satic route via the dhcp eth interface.

[http://www.cyberciti.biz/tips/configuring-static-routes-in-debian-or-red-hat-linux-systems.html](http://www.cyberciti.biz/tips/configuring-static-routes-in-debian-or-red-hat-linux-systems.html)

.

---

