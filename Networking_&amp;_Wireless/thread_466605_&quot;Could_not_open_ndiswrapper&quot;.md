---
title: "&quot;Could not open ndiswrapper&quot;???"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by bkinney on 2007-06-06
I followed instructions from another post to install ndiswrapper and my drivers for Linksys wireless usb adapter.

When I type:

ndiswrapper -v

I get:

utils version: 1.9
driver modinfo: could not open ndiswrapper: no such device

Huh?

- BK

---

### Post by bkinney on 2007-06-06
Ok...I got a little trigger happy.  I switched to the folder that contains ndiswrapper and get more info:

utils version: 1.9
driver filename: /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:  1.43
vermagic:  2.6.20-15-generic SMP mod_unload 586

My question I guess is how can I ensure it's working properly?  I see the wireless network I want t connect to on the list but when I try to connect it just hangs...

- BK

---

