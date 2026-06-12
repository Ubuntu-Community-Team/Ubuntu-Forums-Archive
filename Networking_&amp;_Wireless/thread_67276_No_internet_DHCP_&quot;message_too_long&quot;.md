---
title: "No internet: DHCP &quot;message too long&quot;"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by benlila on 2005-09-19
I've just installed Hoary on my desktop, and I can't get internet access.  I just have a regular ethernet plugged into a netgear router.

When I run:

sudo dhclient eth0

I get a message that says send_packet: "Message too long"

My /etc/dhcp3/dhclient.conf has:
request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers,  host-name, netbisios-name-servers, netbios-scope;

Any help?
Thanks!

---

### Post by benlila on 2005-09-22
<bump>

---

