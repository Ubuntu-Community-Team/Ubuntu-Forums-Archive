---
title: "Why IPv6, IGMP, Router Soliciting?"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by Jaiinus on 2008-02-06
So I put Gutsy on my V2000 laptop, and got compiz and wireless working. In the process of working to get wireless functioning I was using wireshark (with drivers the default ubuntu package source was giving me I could see and would send DHCP discovers but not actually get a response at my college). I noticed some wierd packets, and when I came back to my home and got wireless fully functioning the strange packets were still there. For some reason I'm putting out IPv6 router solicitation packets, and IGMP group membership packets. What's the point of these? Are they used to support a service?

---

### Post by sqrt2 on 2008-02-07
Those packets are pretty harmless. ICMPv6 router solicitation packets are used for IPv6 autoconfiguration (network interfaces asking for IPv6 routers to tell them IP address prefixes for global-scope IP addresses). IGMP is the equivalent of ICMP in the multicasting area, the packets probably are related to Zeroconf.

---

### Post by Jaiinus on 2008-02-08
How can I disable IPv6? I don't use it and I'm not a big fan of putting out anything more than I need to when it comes to network configuration.

---

### Post by sqrt2 on 2008-02-08
[indent]alias net-pf-10 off[/indent]
in /etc/modprobe.d/aliases, or alternatively to just disable autoconfiguration, not IPv6 in general (which leaves you the possibility of assigning adresses manually and using link-local addresses),
[indent]sudo sysctl -w net.ipv6.conf.all.autoconf=0[/indent]

---

