---
title: "DHCP Relay and Firewall"
date: 2016-04-08
forum: Networking &amp; Wireless
---

### Post by SCGSGAog on 2016-04-08
Hi,

I was wondering if anyone can advise me on how to setup a DHCP relay on an Ubuntu firewall. So far the only thing that is configured is masquerading and this is working as I can cross between one subnet to the other but I can't get isc-dhcp-relay to work (its installed on the same ubuntu server). Any advise would be greatly appreciated.

---

### Post by SeijiSensei on 2016-04-08
Let's start with the basics.  Do you have ports 67 and 68 open for both TCP and UDP on the side facing the DHCP server?

---

### Post by SCGSGAog on 2016-04-08
Currently everything is open, but I think I know whats wrong (pretty stupid mistake to be fair), the dhcp server did not have the right gateway i.e. its not pointing to the firewall that has the dhcp relay.

---

