---
title: "rt73 looses connection"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Gabriele Persia on 2007-04-20
Hi all,

no matter what driver I use, the connection goes up for few seconds (say one or two minute at most) and than drop. I'm using an USB ralink RT73 wireless adapter (134f:2573).

I've tried with both serialmonkey and ralink driver following instructions found
here:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)
and here:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

No problem installing and modprobing the driver (driver loads, everything seems ok) but after a while the connection drop.
Disabling DHCP, as I red somewhere, didn't solve.

I'll try disabling WEP protection, ...but I'm not interested in a working-open-network ;-)

(Running kernel 2.6.17 on Ubuntu 6.10)


P.S. I had a similar problem months ago with a prism54 PCMCIA card and older kernel (can't remember the version).

---

### Post by darkmoon22 on 2007-04-21
well i solved my problem with [this ]("http://wiki.ubuntu-it.org/RalinkRT73")wiki...
is in italian but it not hard to understand

---

### Post by Gabriele Persia on 2007-04-22
Thank you for the link, I've already been there, just forgot to mention.

The solution is, roughly, the same proposed in the first link ([http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)), and didn't work for me.
Maybe my USB wifi adapter is faulty, I'm going to check booting windows.


P.S. sure for me was not hard to understand, I'm native Italian speaking ;-)

---

