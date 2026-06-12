---
title: "WPA2 / WPA on D-Link G510 - help for new user?"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by ironchefmoto on 2007-05-29
I've seen a helluva lot of D-Link G510 wireless card posts here, and I'm wondering if I should just ditch the card and get a different PCI WiFi adapter, given that I've had no luck in deciphering a single recommended solution for getting this particular card to work.

I installed Ubuntu 7.04 yesterday and ran the recommended updates.

I've installed, via Synaptic, the following packages:
[LIST]
[*]ndisgtk (graphical interface for ndiswrapper setup)
[*]ndiswrapper-common (may have been installed by default)
[*]ndiswrapper-utils-1.9
[/LIST]

I downloaded the WinXP driver for the G510, which is being listed as follows by lspci:
[LIST]
[*]04:07.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
[/LIST]

When I tried to use ndisgtk to install (the netA3AB.inf driver file), I received the following error message:
[LIST]
[*]sh: Syntax error: "(" unexpected (expecting "}")
[*]module configuration already contains alias directive
[/LIST]

I've read a few things about madwifi, which appears to be installed by default, but I'm wary (as a complete linux newbie) about doing too much command line configuration.  I'm all about the GUI.  ;)

Any suggestions?

Thanks,
IronChefMorimoto

---

### Post by ironchefmoto on 2007-05-29
I should mention that I'm running WPA2 off a linksys WRT54GL running DD-WRT.  I cannot  get a connection with WPA or WPA2 using the default network connection icon that installs with Ubuntu 7.04 (Feisty).  Here's the detailed printout of the lspci command:

[LIST]
[*]Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
[*]Subsystem: D-Link System Inc D-Link AirPlus G DWL-G510 Wireless PCI Adapter(rev.B)
[*]Flags: bus master, medium devsel, latency 168, IRQ 20
[*]Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
[*]Capabilities: <access denied>
[/LIST]

Again -- suggestions are welcome.

Thanks,
IronChefMorimoto

---

### Post by aldomontoya on 2007-05-30
Check this link outL

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

worked straight away. i sepnt 3 days trying other ideas, this worked perfectly. let me know if it works.

---

### Post by ironchefmoto on 2007-05-30
> **aldomontoya said:**
> Check this link outL

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

worked straight away. i sepnt 3 days trying other ideas, this worked perfectly. let me know if it works.

No joy.

This is really disappointing.  There are still 40 different ways (I'm using hyperbole out of frustration here) to do something with terminal commands just to get something simple like wireless working.  Grrr...as a total Linux newb with enough computer building/installing experience to know that this SHOULD BE simpler, it's disappointing.  :(

If anyone else has any suggestions, chime in.  If I can't get wireless working (due to my home office layout -- the CAT5 cable across the room is temporary), Ubuntu 7.04 is gonna be getting dusty on this partition...

Thanks,
IronChefMorimoto

---

