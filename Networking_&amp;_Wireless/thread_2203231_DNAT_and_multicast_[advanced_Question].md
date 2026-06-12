---
title: "DNAT and multicast [advanced Question]"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by povlhp on 2014-02-02
Hi,

I have a Linux machine, it works as a router/gw between my internal LAN and the Internet.
I am using it to look at IPTV with an IPTV box.

My IPTV box has many channels I don't use, and there are other channels not in its channel list, which I can still receive over multicast with a client like VNC. It is running igmpproxy.

How can I map traffic, such that requests to multicast:    233.1.2.3:1234  is actually going to 233.1.2.4:1234 instead ? And that I NAT the multicast address on the way back as well ? Can I do this with iptables ? 
Or do I need to modify igmpproxy as well ? If I fix IGMP proxy what iptables rules are the needed ?

---

