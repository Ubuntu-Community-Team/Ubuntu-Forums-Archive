---
title: "Restricted driver manager asking me for path to firmware for broadcom 4311 wireless"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2008-02-27
A friend of mine recent begun having problems connecting his laptop to his wireless network.  I was originally able to get his card working after a fresh install by downloading all of the latest updates and enabling the restricted driver for the wireless adapter.

But when he brought his laptop by today, his wireless adapter would not detect any wireless networks nearby.

So my first thought was to use a LAN connection to my router and download all the latest updates again, since there were many available (including a kernel update).  I also disabled the restricted driver itself before doing any of this, since my days of using windows gives me this "re-install it in an attempt to fix it" reflex.  Anyway, I hope I haven't dug myself in deeper by doing that.

Anyway, after installing all the updates, and upon re-enabling the restricted drivers for the wireless adapter, I get the following message box (see attached screenshot).

"Please specify where firmware can be found"

If I tell it to use the Internet location, it says the location specified is invalid.

So what do I do now?

---

### Post by diablo75 on 2008-02-27
Well, I managed to get the firmware file selected after downloading it, then using a sudo mv command to get it into my root folder (because it didn't want to browse to my own desktop).

But the wireless card doesn't work.  The restricted driver says it's enabled.  But it's simply not working...

How should I go about fixing this?

---

