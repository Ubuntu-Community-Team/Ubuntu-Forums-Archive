---
title: "Wireless occasionally won't connect--retrying works--troubleshooting?"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by EricDB on 2008-02-06
I'm using WPA on my home WLAN.  Usually Ubuntu 7.10 connects to it just fine, but once in a while, NetworkManager stalls for about 30 seconds with one green light, then aborts back to "not connected".  Retrying once or twice always gets me a connection, but how can I investigate what's causing it to fail occasionally?

The AP is right across the room from my easy chair; signal strength isn't an issue.

---

### Post by jan quark on 2008-02-06
what is your network card ?

have your tired another network applet like wifi radar?

---

### Post by EricDB on 2008-02-06
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I'm not using ndiswrapper.

I'll try WiFi Radar and see if it behaves any better.  Thanks for the reply!

**Edit:**WiFi radar wouldn't connect.  It asks for a WPA driver (not sure what I need there--I'll have to research it).  It didn't seem as nice as NetworkManager, though...no panel icon?

---

