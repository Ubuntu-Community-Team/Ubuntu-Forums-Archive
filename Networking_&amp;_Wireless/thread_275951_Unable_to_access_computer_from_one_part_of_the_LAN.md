---
title: "Unable to access computer from one part of the LAN"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-10-12
In our place , we have two networks going,
One wired network,
one wireless,

A debian system acts as the router,
it connects to the wireless router,
the wired Switch and the ISP,

From the wired network, we are able to
ping the wireless router, but are not able to
access/ping ppl using the internet through the wireless router...

Are we doing somehting wrong..or do we need to configure
something somewhere??
Please guide me

---

### Post by mal on 2006-10-12
Hellmet,

I'm no expert, but it sounds to me like you need to configure your wireless router as a "bridge".

A router will normally block access from the internet side to the connected clients.  This is an advantage when the router is connected directly to the internet, as it protects the clients from unauthorised access.  In this case it would prevent access from your wired network to the wireless network.

To set up the router in bridge mode, you will need to read the manual.  I'm not sure whether all routers are capable of this.

Hope this helps,

Mal

---

### Post by hellmet on 2006-10-12
the thing is that... the wireless router is connected to the Debian router for
its internet, it only serves the two wireless laptops..
won't the configuration change if I change the mode that way??

Do I need to add IPTABLEs to the Debian router??

---

### Post by mal on 2006-10-12
Hellmet,

Sorry, but I can't really help much more without a lot more details about your network configuration.  However, here are a few suggestions:

Your wireless router would provide a separate sub-net (with a different IP address range) for the connected laptops and would not allow access to them from the debian router.

You might be able to use "port forwarding" on the wireless router to get access to one of the laptops, but it would be better if the wireless router could be set up for "bridge mode".  This would allow the wireless laptops to use the same IP address range as the clients connected to the debian router and they would be able to connect to each other.

I don't think there is anything that you could do with IPTABLES on the debian router that would help.

On my system, I have a modem/router connected to the internet and a wireless router (which also has hardwired switched ports) for laptops.  The wireless router is configured to the same IP address range as the modem/router and has DHCP disabled.  The connection to the modem/router is via one of the hardwired client connection ports rather than the normal router uplink connection.  The modem/router provides the DHCP service.

You might be able to do something similar with your system.

Regards,

Mal

---

