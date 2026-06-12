---
title: "Avahi VLAN limitations?"
date: 2014-01-14
forum: Networking &amp; Wireless
---

### Post by sderby on 2014-01-14
I've recently set up a lubuntu box as a bonjour gateway for airplay across 23 vlans.  It looks like there's a limit of 20 VLANs working first in, first out as IPs are grabbed via DHCP on the interfaces.

Is this an undocumented limitation (I couldn't find anything) and working as intended?  Is there something in the avahi-daemon.conf file I need to modify?

Any help is appreciated.

---

### Post by sderby on 2014-01-21
Turns out there's a default limit of 20 IGMP memberships in Linux.

To fix, open:

[FONT=lucida console]/etc/sysctl.d/avahi-igmp-max.conf[/FONT]

add the line:

[FONT=lucida console]net.ipv4.igmp_max_memberships = 50[/FONT]

then run:

[FONT=lucida console]sudo sysctl --system[/FONT]

---

