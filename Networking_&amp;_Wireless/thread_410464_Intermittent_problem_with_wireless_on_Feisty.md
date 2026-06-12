---
title: "Intermittent problem with wireless on Feisty"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by albs on 2007-04-15
Guys, I have a problem with Feisty... please note that the same hardware config worked perfectly on Edgy.

Sometimes wireless connects, but most of the time is doesn't... and issuing the iwconfig command, I get this:

[ 511.381147] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 513.380892] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 523.493792] ndiswrapper (set_essid:60): setting essid failed (C0000001)
[ 524.080670] wlan0: no IPv6 routers present
[ 540.431964] ndiswrapper (set_essid:60): setting essid failed (C0000001)
[ 551.455140] ndiswrapper (set_essid:60): setting essid failed (C0000001)
[ 562.490306] ndiswrapper (set_essid:60): setting essid failed (C0000001)
[ 587.935505] ADDRCONF(NETDEV_UP): wlan0: link is not ready

I use a Marvell 88w8335 Libertas chipset, and use WPA-Personal for authentication.  On the "Windows Wireless Drivers" tool, it says "Hardware present: no", but that's the case even when wireless works (which it does sometimes).

Any tips?

---

### Post by nautilus on 2007-04-16
if it were me, i'd apt-get remove ndiswrapper, and install my own. (in fact, i did, 1.41 here)

but this is generally more advanced than the average new kid to linux may be comfortable with... in any case, it seems like ndis is having some difficulty there, not linux or the network stack in any noticible way.

---

