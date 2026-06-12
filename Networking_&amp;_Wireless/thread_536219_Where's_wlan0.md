---
title: "Where's wlan0?"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by Jerryonimo on 2007-08-27
I have a Gateway ML3109 laptop loaded with Ubuntu 7.04 and a Belkin G wireless card.  Just a few days ago, I had the interface wlan0 for wirelss networking.  Now it's called eth1 and I get an error message saying that there's no profile in /etc/proc/dev.  I can promise you I never touched that folder or deleted anything to do that.
The funny thing is, I can go into "Network" and configure the interface.  It detects networks just fine, but for some reason I can't apply any of the changes.
Please help.  I'm desperate.:shock:

---

### Post by Zorael on 2007-08-27
```
$ lshw -C network
```

Does that list your interface as eth1 or wlan0? I'd put my money on lshw's word. :)


edit: I recommend wicd over the standard network managers. Get it [here](http://wicd.sourceforge.net).

---

