---
title: "network interface spontaneously changed and broke"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by moshy on 2007-07-22
My wireless internet has been working with no problems until a few days ago it stopped working. I couldn't figure out why, but I discovered that a new interface had been added randomly spontaneously ra0:avahi, and this is what it is trying to connect to now. Before doing ifconfig would get be lo, eth0 and my wireless (Ra2460/2400 I think) which was just plain old ra0.
Now clicking on Network Monitor gets me this

Could not find information on interface 'ra0:avahi' in /proc/net/dev

Which makes sense cause i looked at this file and it only had lo, eth0 and ra0. I've got no idea why this avahi thing has suddenly taken over.
The weird this is I would normally live cd my way out of things like this, yet i try that and the exact same problem occurs, off a compact disc! when before i would be able to use ra0 off the cd.

---

### Post by ddrichardson on 2007-07-22
Has there been any changes with your router?

---

### Post by moshy on 2007-07-24
no the router is in my room

---

### Post by moshy on 2007-07-24
its solved, my brother ended up secretly putting a password on the network without telling me

---

