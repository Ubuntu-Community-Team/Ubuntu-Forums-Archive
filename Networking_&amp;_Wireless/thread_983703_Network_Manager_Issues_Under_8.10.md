---
title: "Network Manager Issues Under 8.10"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by cjeness on 2008-11-16
I upgrade from 8.04 to 8.10.   I have a laptop computer with both a wired and wireless lan connection.   Normally, I do not have the wired connection plugged in.   After the upgrade, I no longer see the Network "strengh" applet.   I eventually located a network configuration option under preferences; however, if I attempt to make any changes, then I receive the following error:

Updating connection failed: nm-ifupdown-connection-c.82 - connection update not supported (read-only) ...

At home I use static IP addresses; however, when I take my computer offsite, I need to switch to the "roaming" mode for wireless.   How do I make this work under the new Network Manager?

---

### Post by jml75 on 2008-11-16
Hi,

I have the same problem that you have.

Any one knows what the problem is?

---

### Post by JoshuaJamZ on 2008-11-18
Same here as well... I was able to get back online by manually changing /etc/network/interfaces to DHCP and /etc/init.d/networking restart ... then switching it back to static and restarting again.

However, this error still occurs when attempting to change via System>Preferences>Network Configuration:

Updating connection failed: nm-ifupdown-connection-c.82 - connection update not supported (read-only)

Netmask has been changed simply to 24 and any attempt to change it produces the above error.

I also notice that the networking icon has disappeared from my panel. This is very odd.

This has happened to me twice now, btw, since upgrading to 8.10.

Even though the network is currently working, something isn't right here... anybody know what and how it can be fixed?

---

### Post by poldie on 2008-11-18
> **jml75 said:**
> Hi,

I have the same problem that you have.

Any one knows what the problem is?

No idea if this is any use, but after having several problems with Network Manager I took someone's advice here and installed WICD and have had no problems since.

---

### Post by kracheck on 2008-11-18
I use WPA with Static IP addresses via a Linksys WRT54G router.  On numerous occasions I have tried and managed to have my wireless work but never through the NetWorkManager applet. I have applied Wieman's WPA guide (check the forum) on /etc/network/interfaces and untill Ubuntu 7.10 that solved the problem.

With Ubuntu 8.04 I have tried WICD (wicd.sourceforge.net) and I must say I'm impressed with it. It works like a breeze. No more long manual configurations of the interfaces file, install, configure and surf.

---

