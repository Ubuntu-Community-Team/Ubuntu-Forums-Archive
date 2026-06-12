---
title: "Kismet stops receiving packets"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by cune on 2007-09-09
Hello,
I have Kismet set up on my Prism 2.5 card, using the HostAP driver.

Kismet works fine for a good while, usually 20-50 minutes, then stops receiving packets. The Kismet server seems to stop communicating with the interface, as it won't display the Wireless card power level (shortcut: l).

Kismet does seem to work properly apart from this.

I have tried disabling NetworkManager and NetworkManagerDispatcher, as well as killing the dhclient3 process. No change. It looks like something is interfering with the Kismet server, but I don't know what.

Any ideas?

---

