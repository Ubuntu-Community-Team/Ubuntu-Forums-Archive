---
title: "xsupplicant 1.2.1"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by MrJavalava on 2005-10-19
Hi all..

Having some trouble going from 1.0.1 to the recent 1.2.1

What happens is actually nothing.

The XSupplicant doesn't read the configuration file or start the network card, it just say "starting XSupplicant 1.2.1" and it annoys me!

The configuration to start the xsupplicant is <xsupplicant -i eth0 -c /etc/xsupplicant/xsupplicant.conf>
Those of you who already noticed; yes the configuration file doesn't really need to be in the startup of xsupplicant since it's in the default directory, but I do it anyway to be sure.

The odd thing is the fact that the 1.0.1 starts up cleanly and works, if I startup with the recent version of xsupplicant the internet connection shuts down.

By the way, how do you hold back a update in apt?

Any ideas?

---

### Post by bytec0de on 2005-11-17
The configuration file syntax has changed. Enable debug to check for errors:

> xsupplicant -i eth0 -c /etc/xsupplicant/xsupplicant.conf -d A -f

---

