---
title: "Wireless quit connecting on Ubuntu partition"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Weidbrewer on 2008-11-16
My wireless was working fine until half-time today, when it suddenly quit and wouldn't reconnect on my Ubuntu partition.  Still works fine on my Windows partition of the same machine, as well as two other laptops in the house.  Wired connections are all still working perfectly fine.  

This laptop is running 8.10.   Anyone have any suggestions?

---

### Post by jnorthr on 2008-11-16
you might try the 'ifdown' command followed by 'ifup' to stop and re-start your network. Read the man pages first. A wild guess - did your ubuntu network have a 'lease' on the i/p connection that expired ?

You might look into your system logs at System>Administraton>System Log and review messages and syslog entries to gain some clues. Mine showed something like :
[COLOR="Red"]
Nov 17 00:11:32 tiny NetworkManager: <debug> [1226880692.145386] periodic_update(): Roamed from BSSID 00:3W:F1:FW:F8:A4 (Fred_France) to (none) ((none)) 
[/COLOR]
seems like my wireless card is hunting for a new connection every so often, yours may too.

---

### Post by Weidbrewer on 2008-11-16
Yeah, those things had crossed my mind as well.  Nothing was working, which is why I came in here - I was totally stumped.

Well, I ended up clearing out the save WEP key, shutting down the laptop, resetting the router, booted it back up and re-entering everything.   That worked.  I got nothin'.   Thanks for chiming in, thought!

---

