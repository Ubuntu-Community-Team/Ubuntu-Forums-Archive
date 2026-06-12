---
title: "Firefox bouncing from offline to online modes"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by bogdanbiv on 2008-08-02
After startup and login Firefox keeps going from offline and online mode without loading any page. The bug seems similar to the one reported here
[Launchpad #86680]("https://bugs.edge.launchpad.net/ubuntu/+source/knetworkmanager/+bug/86680/"), only that I have removed the knetworkmanager package from my system, but the bug is still present.

The bug seems to affect only Firefox (v3.0.1) and not Konqueror+Kopete, which works normally. (maybe it does not affect Konqueror because I removed the knetworkmanager package?)

Oh, and the bug is reported to reproduce only for ppp connections.
I have a PPPoE connection (PPP over Ethernet), configured with pppoeconf.

I run Kubuntu 8.04 with the latest updates.


```
$ uname -a
Linux bog-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
```

---

