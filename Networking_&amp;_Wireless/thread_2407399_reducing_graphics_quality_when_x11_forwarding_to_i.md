---
title: "reducing graphics quality when x11 forwarding to increase speed"
date: 2018-12-03
forum: Networking &amp; Wireless
---

### Post by carneiroid on 2018-12-03
Hi,
Im curious, is there any way to do reduce quality this , say reduce colours to 256 or even greyscale and reduce pixels as well to speed up x11 forwarding
thanks

---

### Post by TheFu on 2018-12-04
Use **x2go** which does have compression and color controls.  I've used it from 5 continents with as slow connections as 128Kb ISDN.  x2go is based on the NX protocol, which includes an ssh tunnel in the protocol.

Over the decades, low-bandwidth X11 never took off.  Basically, if you don't have 100 Mbps connections between the 2 systems or faster, don't use X-forwarding.

---

