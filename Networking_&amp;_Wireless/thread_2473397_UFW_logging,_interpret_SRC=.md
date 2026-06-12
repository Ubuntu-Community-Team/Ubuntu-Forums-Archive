---
title: "UFW logging, interpret SRC="
date: 2022-04-03
forum: Networking &amp; Wireless
---

### Post by paul.a on 2022-04-03
After quite some time looking around, I still cannot interpret the source **SRC=** in the following entry (repeats about every twenty seconds, my be a bot that I want to identify.  The MAC address does not find a manufacturer.)
[INDENT]Apr  3 14:48:49 server6 kernel: [401124.076959] [UFW BLOCK] IN=enp3s0 OUT= MAC=33:33:00:00:00:01:d0:21:f9:40:17:70:86:dd **SRC=fe80:0000:0000:0000:d221:f9ff:fe40:1770** DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=236 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=48227 DPT=10001 LEN=196
[/INDENT]

Note log level low, high and full all give the same entry

---

### Post by Doug S on 2022-04-03
Disclaimer: I am not a IPV6 expert.

Those look like link local and multi-cast addresses. So I think everything is internal to your LAN.

---

### Post by The Cog on 2022-04-03
fe80:0000:0000:0000:d221:f9ff:fe40:1770 is an IPv6 address. It is likely autoconfigured by an interface with the MAC address d2:21:f9:40:17:70 by inserting ff:fe in the middle. You might be able to find that MAC address in your IPv4 ARP table to find out what machine is sending it. tcpdump or wireshark should be able to tell you more.

---

### Post by paul.a on 2022-04-03
Thank you, Doug S and The Cog.  Yes, it's a new Ubiquity 48 PoE switch, "installed" physically, but no software, by a vendor Friday afternoon.  I found the entry doing my regular Sunday security check -- it announces itself in the ARP tables with a "?" (no name) and has grabbed itself a dhcp on the LAN.  Now have to look into IPV6 local and multi-cast addresses and find out what it's doing -- apart from flooding the UFW log and apparently not getting caught in either syslog nor auth.log... Oh well...

---

