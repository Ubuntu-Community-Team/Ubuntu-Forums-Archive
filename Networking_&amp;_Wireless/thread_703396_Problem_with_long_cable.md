---
title: "Problem with long cable"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by Agren on 2008-02-21
I have the following problem, I'm really clueless as to what's causing it:

My setup is this:
Ubuntu server
One long ethernet cable, ca 30 meters
One short ethernet cable ca 5 meters
One windows XP machine

If I connect the Ubuntu server using the short cable everything works fine, I get network access directly at startup
If I connect the windows XP machine using the long cable everything works fine, I get IP adress and network access
If I connect the Ubuntu server using the long cable (and using the same jack on the router as above) it can not find the network. On startup the network does not get enabled and if I try to do it manually it tries a while then tells me it can't find a DHCP server.

Anyone have any help to give me?

---

### Post by jeffus_il on 2008-02-21
I would guess that the long cable is problematic, maybe has some kinks in it or passes close to electricity supplies transformers or some noisy interference. But nevertheless Linux should do what windows does, so there must be some form of software difference. I would look at the driver parameters, and look for a timeout that is set too short and does not manage to connect after a slow response. Could be a dhcp timeout as well. The easiest workaround is to lower the line speed, e.g. from 100MBits to 10 MBits. Maybe windows is falling back to a lower speed.

---

### Post by Agren on 2008-02-21
Yeah, but the cable is only around 30 meters, if that, should be well inside of the limits. But anyway, stepping down in line speed is of course a good advice, I should have thought about that myself :)
I don't think that's what windows does, though, at least it states connected at 100 Mbit.

---

