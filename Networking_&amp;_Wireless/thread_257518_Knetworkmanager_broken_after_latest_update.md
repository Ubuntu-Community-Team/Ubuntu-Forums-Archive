---
title: "Knetworkmanager broken after latest update"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by spiderworm on 2006-09-14
Hi,

I just did an update that updated both knetworkmanager and the kernel.  Now knetworkmanager no longer displays any wireless networks.  It does still seem to recognize my wireless card, tho.

spiderworm

---

### Post by K0LO on 2006-09-16
I think that after the update the list of access points that knetworkmanger had previously associated with was cleared.

After updating, I had to manually add back all of my desired access points using "Connect to Other Wireless Network...". After adding them back, they're all displayed again.

However, the update also caused another little cosmetic problem. The tray icon for knetworkmanager displays a signal strength bargraph correctly. When you click on the tray icon it used to display bargraphs for the signal strengths of all of the access points in radio range. After the update, the outlines for the bargraphs are there but no bars!

*Edit -- the "no bars" problem is apparently related to my display theme. I'm using the Widget Style "Keramik". If I turn off "Animate Progress Bars" the knetworkmanager bars return. Choosing other styles also results in visible signal strength bargraphs in knetworkmanager, even with "Animate Progress Bars" enabled.

---

