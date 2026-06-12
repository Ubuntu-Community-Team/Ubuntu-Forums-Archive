---
title: "[SOLVED] wireless signal poor"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by mandrill on 2007-10-02
been all around the forums, and google. no sweetness...

netgear wpn311, 20 feet from router, line of sight, signal never over 38%, lots of disconnects, - same card 5 feet away on windows, signal 90%, never disconnects.

wiki says wpn311 doesn't like wpa, re-set it to wep, lost 10%

somebody has got to know how to fix this.......

---

### Post by Lambert on 2007-10-02
> **mandrill said:**
> been all around the forums, and google. no sweetness...

netgear wpn311, 20 feet from router, line of sight, signal never over 38%, lots of disconnects, - same card 5 feet away on windows, signal 90%, never disconnects.

wiki says wpn311 doesn't like wpa, re-set it to wep, lost 10%
[B]
somebody has got to know how to fix this[/B].......

There are bug reports on the madwifi driver site with no answer on how to fix this. You can read them [here. ]("http://madwifi.org/ticket/1343")
Notice the link inside to another page called #705. If you find an answer it will be at that sight or with the developers of the driver.

One fix mentioned there is to scrap the native driver and go with ndiswrapper.

---

### Post by mandrill on 2007-10-02
> **Lambert said:**
> There are bug reports on the madwifi driver site with no answer on how to fix this. You can read them [here. ]("http://madwifi.org/ticket/1343")
Notice the link inside to another page called #705. If you find an answer it will be at that sight or with the developers of the driver.

One fix mentioned there is to scrap the native driver and go with ndiswrapper.

Kinda looks that way........thanks for the heads up.....

---

