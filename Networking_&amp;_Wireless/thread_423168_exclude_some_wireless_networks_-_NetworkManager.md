---
title: "exclude some wireless networks - NetworkManager"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by merry_meerkat on 2007-04-25
Hi,
I am using NetworkManager to connect to my wireless router, which is secured (WPA). My neighbour seems to have an unsecured wireless network running. Since the reception of my router is better, since I have more control over it, and because I have paid for it, I would like to connect to my own network. Sometimes this works just fine. However, most of the time, NetworkManager fails to connect, and instead connects to my neighbour's unsecured network. Often it seems to do so without even bothering to try to connect to my router.

Is there a way to tell NetworkManager to not connect (to exclude) automatically to certain wireless networks (by e.g. SSID), to force it to connect to my network?

THANKS!

---

### Post by spd106 on 2007-04-26
This isn't directly possible at the moment though you can stop re-connecting to an network by removing it from gconf. This FAQ will tell you how [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

---

