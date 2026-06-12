---
title: "Using Ubuntu 6.10 Server w/ Telewest Cable ISP"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by SiR GadaBout on 2006-11-24
Hi,

Does anyone have any experience setting up Edgy Eft Server with Cable Telewest over ethernet using dhcp, especially through the Motorola modem?
I've had no luck and unable to discover why.

SiR G.

---

### Post by hairshirt on 2006-12-03
Hi,

I've just fallen apon your post.  Would a previous post I made help?  [http://www.ubuntuforums.org/showthread.php?t=283628](http://www.ubuntuforums.org/showthread.php?t=283628)

Let me know

---

### Post by SiR GadaBout on 2006-12-03
Hi,

Though I've not double-checked, I think the problem was that I had to reset my cable modem before attempting to use it with a different computer.  I think it has something to do with the way DHCP is implemented.  Though, as I say, I haven't confirmed this, I think the solution is to switch of the modem before attaching it to the Ubuntu box, then switching it on, and then booting the Ubuntu box.  This allows the Ubuntu box to renew its DHCP lease.
I discovered this after finding that my iBook wouldn't connect through the modem after succesfully using it with the Ubuntu box.  It wouldn't renew the lease either, so I simply rebooted the cable modem, and the iBook was able to renew the lease and reconnect to the web.
One problem down - 2 more to go (at least): getting my printer working with CUPS; and getting NFS working.
Thanks for your input.
SiR G.

---

