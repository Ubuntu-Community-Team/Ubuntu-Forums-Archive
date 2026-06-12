---
title: "Using ethtool to manually set ethernet speed"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by RChickenMan on 2007-10-17
Good day,

I need to set my wired ethernet to communicate at 10 mbps (as opposed to 100 mbps).  I am trying to talk to an embedded device acting as a server which runs at 10 mbps, and the only way to do so is for the client ethernet device to talk at the same speed.  I have tried using ethtool to manually set this speed:

sudo ethtool -s eth2 speed 10

When I check to see if it worked (using ethtool again) it seems that the setting sticks for about a few seconds, then reverts back to 100 mbps.  I have tried all kind of combinations of changing the speed with the device disabled and such.

Why would this setting not stick, and how would I go about making it do so?

Thanks for any help you may be able to provide!


p.s. Why the hell am I doing this?  That's right... I'm an engineering student...

---

### Post by noob12 on 2007-10-17
You also need to turn autonegotiation off:

```

sudo ethtool -s eth2 speed 10 autoneg off

```

---

### Post by RChickenMan on 2007-10-18
Turning autonegotiation off prevents it from establishing any connection whatsoever.

---

