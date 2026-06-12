---
title: "Large packets over tunnels with smaller MTU ?"
date: 2015-08-07
forum: Networking &amp; Wireless
---

### Post by povlhp on 2015-08-07
[FONT=Verdana]I have an IPTV box, and would like to tunnel traffic to it over a tunnel (my MoCA link limits multicast to 10 Mbps which is not good for HDTV). I have created a GRE tunnel and bridged it with the IPTV VLAN, but all large packets are dropped.[/FONT]
[FONT=Verdana]I can see the packets do have the DF (Don't Fragment) bit set.[/FONT]
[FONT=Verdana]How can I bridge large packets over a tunnel ? Is there a lightweight tunnel type that silently fragments and reassembles packets ? I know the ISPs does this over ATM over DSL, as it has a very small frame size (53 bytes).[/FONT]
[FONT=Verdana]Can I clear the DF flag and expect success ? How can I do this ? They are coming in on eth0.3, which are part of the gre-bridge curently not working.
I have bandwidth for overhead of fragmented packets.[/FONT]
[FONT=Verdana]I don't know if the multicast packets has the DF flag (not part of my dump this time around).[/FONT]

---

