---
title: "problems with azureus- is avahi the reason?"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by johnny1978 on 2007-04-09
Hello all,
Since I upgraded to 6.10 I have had problems with networking. At the beginning it didn't let me use the wireless, although that problem has been taken care of. Now, when I use azureus, it always says it I am firewalled, even though I have already configured the iptables, activated upnp in azureus, forwarded my tcp port, and configured a static ip address.
Since all these has been covered, I am thinking that Avahi Daemon may have something to do with this, since when I shut down my laptop everything turns off in the right way, except Avahi daemon. This is what it appears on screen:

Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon [fail]

Everything turns off ok, (except the RAID arrays, but that's another matter and another thread)

What do you guys think?

---

### Post by spd106 on 2007-04-09
I don't see how avahi could affect bittorrent or iptables. But who knows, it might be worth investigating. 

You can disable avahi in the network-admin capplet. Untick the service discovery box under the General tab. Nothing relies on avahi yet, accept perhaps DAAP sharing.

---

