---
title: "connection pauses about every 2 minutes"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by kdotsky on 2006-11-25
I've had this problem for quite some time now and haven't the slightest clue how to figure out what's going on.

My connection periodically (every two minutes) stops working at all for several seconds.  The wireless connection appears to be intact.  I don't have to reconnect to my wireless router (no security) when it happens.  After a few seconds the connection just starts working again.

The problem is particularly annoying in SSH sessions, where I can't type anything for a period of time.  For web browsing it usually just appears as a slow loading page.

Here's an image showing the traffic and the periodic stalls.

[ATTACH]19974[/ATTACH]

I'm running dapper.  Here's info about the wireless card:
0000:01:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
        Subsystem: Belkin: Unknown device 700c
        Flags: bus master, medium devsel, latency 168, IRQ 209
        Memory at feae0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2


Thanks.

---

### Post by spd106 on 2006-11-25
Hi, I used to get this before edgy when I had network-manager installed. I believe it was caused by the "background" scanning. It wasn't implemented in the old madwifi driver, instead the connection would drop while it scanned. This has been solved in the madwifi-ng driver and it's not a problem for me in Edgy.

You could try compiling madwifi-ng from source, [http://madwifi.org](http://madwifi.org).

---

