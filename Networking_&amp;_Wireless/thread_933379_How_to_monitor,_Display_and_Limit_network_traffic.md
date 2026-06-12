---
title: "How to monitor, Display and Limit network traffic?"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by bliffle on 2008-09-29
I have a new EVDO connection with a 5gb/mo. limit and the tools for displaying usage are slow, tardy and inaccurate.

What tool can I use to monitor and display my usage, and perhaps even limit it to my 5gb. quaota?

---

### Post by nixscripter on 2008-09-29
Display and limit are two different things.

For what it's worth, display is actually really easy, depending on what you want to track. ```
ifconfig **eth-whatever**
``` will include transmitted (TX) and recieved (RX) bytes since the interface was create (i.e. at boot time).

Limiting might be possible with traffic shaping, but that's complicated: [http://lartc.org/lartc.html](http://lartc.org/lartc.html)

---

