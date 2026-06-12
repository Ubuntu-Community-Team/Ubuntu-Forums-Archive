---
title: "is there an app that lets you scan channels?"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Atomic Dog on 2007-06-26
I have an office with seriously about 12 wireless stations.  Some are ours and some are other companies in the building.  I'm having an issue with one and would like an app that scans the wireless frequencies and tells me what is in each channel.  There are Windows apps that do this, NetStumbler for instance, but is there a linux app that does?

---

### Post by tturrisi on 2007-06-26
open a terminal and do:
iwlist ethX scan
where ethX= your adapter

---

