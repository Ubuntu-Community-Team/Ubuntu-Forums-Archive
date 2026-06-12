---
title: "RTL8139C lagging Edgy desktop"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by Metalrat on 2007-01-02
I'm getting bad delays when Edgy desktop is loading,  and with apps loading in general.

I've found that disabling eth0 fixes this, *but the adapter itself is working fine*, especially since I disabled IPv6 (no big loss!).

My system is a Shuttle SB61G2 with onboard Realtek 8139C 10/100 ethernet.
I connect through a D-Link broadband modem/router, but I *think* the problem is local to my machine.

Please help, this is ](*,)  time!

---

### Post by Metalrat on 2007-01-04
I've managed to narrow this down a bit, it seems that as soon as I enter DNS info for eth0 the problem kicks in. I usually use the DNS forwarding service of my D-link router/modem (a DSL504-T), so enter the router's IP as the DNS.

My network has DHCP disabled, with 3 static IPs set up, usually just one or two in use.

I'm "flying by the seat of my pants" here, trying everything I can think of but still a Linux noob. :confused:

---

### Post by Metalrat on 2007-01-17
Further work leads me to believe this is something to do with SMB (HAL fails if I log-in too quickly)

Not had time to look up and apply fixes yet.

---

