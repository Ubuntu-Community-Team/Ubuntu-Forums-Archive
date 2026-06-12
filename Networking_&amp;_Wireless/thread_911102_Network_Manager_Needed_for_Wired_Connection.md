---
title: "Network Manager Needed for Wired Connection?"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by infoseeke on 2008-09-05
Hey guys, I've seen a lot of posts on Network Manager regarding wireless cards and connections, but not much on the necessity of it regarding a wired connection. Is it really needed to properly bring up the network interface? And will removing it affect anything else?

I kind of feel that it's just taking up system resources. Not to mention how it's annoying after resuming from hibernation - takes forever to "connect" and never brings the interface up properly.

Can this me removed without replacing it with anything?

---

### Post by dodle on 2008-09-05
I think NM is required to connect to the internet, but I'm not 100% sure.  If it does have to be replaced by something, you can try Wicd, which I don't like very much, but others like it better than NM.

Edit:  If you uninstall networkmanager-gnome, it will delete the applet that loads in your taskbar at startup, but will leave the NM core so that you can still connect with a wired connection.

---

