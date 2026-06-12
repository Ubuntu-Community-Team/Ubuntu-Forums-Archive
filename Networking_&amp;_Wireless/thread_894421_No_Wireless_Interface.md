---
title: "No Wireless Interface?"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by philentropist on 2008-08-19
I just installed 8.04 LTS on my friend's acer 5570z.  It has a atheros wireless card of some sort, but no interface is showing up for it.

The hardware manager says that "Atheros Hardware Access Layer" and "Support for Atheros 802.11 wireless LAN cards" are both enabled and in use.  I also checked lsmod, which shows that ath_pci is loaded.  Still, ifconfig -a only shows the wired adapter.

I've already tried [HOWTO: Atheros wireless, including AR5007EG]("http://ubuntuforums.org/showthread.php?t=792158") but the code wouldn't compile.  Anyone have any ideas?

---

