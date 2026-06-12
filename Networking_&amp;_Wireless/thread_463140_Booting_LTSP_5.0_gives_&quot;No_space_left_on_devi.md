---
title: "Booting LTSP 5.0 gives &quot;No space left on device&quot; errors related to nbd-client"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by tlevine on 2007-06-03
LTSP 5.0 almost works for me.  The client is able to connect to the server and start loading the operating system, but pretty early on, when the sound device is being configured, I start getting "No space left on device" errors when mknod is run.  Most of the errors seem to involve network block devices; I remember seeing /dev/nbd1 to /dev/nbd15..  At the end, it says something about nbd-client and tries to start X but fails.

X probably fails just because nothing has loaded, so does anyone have any ideas about what's wrong with the network block devices?

---

### Post by tlevine on 2007-08-20
I just added some RAM, and it works now.  I think I needed a total of about 360mb of RAM to load everything but only had 32mb.

---

