---
title: "network &quot;unclaimed&quot; after a disk integrity problem"
date: 2016-08-17
forum: Networking &amp; Wireless
---

### Post by theshanman on 2016-08-17
I no longer have networking because I somehow got a disk integrity problem and though it tried to repair the problem on bootup, apparently it didn't do it successfully. I'm running 14.04.

Now I have no eth0 but lshw -C network shows my network card. It is listed as "UNCLAIMED". From what I can tell that means the driver isn't loading? The driver does still seem to exist in the kernel/drivers/net/ethernet directory. Maybe the driver itself is messed up? Or is there anything else that would block it from loading or prevent the card from being properly recognized as being associated with that driver (intel e1000 btw)?

This is in vmware and I do have an older snapshot. I'll lose a bunch of changes if I simply go back to that one so I hope to salvage my current state if at all possible. That said, I can go back to the old snapshot to compare/grab files or whatever if that helps. The network does work in that snapshot FWIW.

Appreciate any help!

---

### Post by theshanman on 2016-08-18
Anyone? What could I compare between my "good" snapshot and my "bad" snapshot to find out why the driver isn't loading? I can more or less find my way around in linux but I'm not super knowledgeable and drivers is an example of an area I don't really know at all.

---

