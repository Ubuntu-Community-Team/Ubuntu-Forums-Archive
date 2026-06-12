---
title: "NetworkManager: Ranking networks"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by AusIV4 on 2007-08-23
Is there any way to tell NetworkManager to only connect to one network if another network is unavailable?

I live on a college campus that has ubiquitous wifi. I also have a wireless network in my apartment, which I would prefer to connect to if it's available for a number of reasons. But every time I boot my laptop, it connects to the school's network, regardless of whether or not mine is available. I always have to tell it to connect to my personal network. I know I can use gconf-editor to delete the bssid of networks I don't want to auto-connect to, but I *do* want to auto-connect to this network when my apartment's network is unavailable (I'm on the other side of campus).

KNetworkManager has enough other flaws I consider it unusable, but at least it had a "Trusted" and "Untrusted" category and would connect to a trusted network if it were available.

If this isn't currently possible, is it in the works for future versions?

---

