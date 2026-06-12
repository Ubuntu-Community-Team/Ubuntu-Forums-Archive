---
title: "[SOLVED] Wireless slow at 1Mb/s"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by amorangi on 2008-11-17
The wifi on my laptop was very slow doing transfers, and although Network Manager and iwconfig both reported a connection at 54Mb/s in reality transfers were happening at 1Mb/s. Everything had worked fine in Hardy - the problem started with Intrepid. I tried all the various tricks with iwconfig as suggested in other threads, but since iwconfig was already reporting a 54Mb/s connection none of these made any difference. I was about to see if I could upgrade the driver, but as a second-last resort I tried wicd as a replacement for Network Manager - problem solved.

The default Network Manager has some very serious shortcomings - it should never have been put out to the public in the current state (see static IP address problems).

Hope this helps someone.

---

