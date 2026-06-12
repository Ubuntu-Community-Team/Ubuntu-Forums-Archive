---
title: "Keeping wireless card in &quot;Monitor&quot; mode"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by fiat1100d on 2007-07-02
Hi!

I need to have a wireless LAN card into Monitor mode for tests with security issues, by capturing Wi-Fi management frames, but after some time the card will return into Managed mode by itself.

How should I configure it for having it Monitor in a stable way? Thanks!

---

### Post by tturrisi on 2007-07-02
What card?  What chipset?  What driver?

---

### Post by fiat1100d on 2007-07-02
Card is a 3Com 3CRUSB10075 based on ZyDAS ZD1211b chipset, using patched zd1211rw driver (for using the aircrack-ng tools). Ubuntu 7.04

---

### Post by fiat1100d on 2007-07-04
Does anybody know a solution? Should I leave the card "floating" with no configuration parameters in /etc/network/interfaces (but in this way it doesn't work) or should I make some particular configuration?

Thanks!

---

### Post by tturrisi on 2007-07-04
Probably has to do w/ network-manager taking control of the interface.  I never use network-manager as I believe it's buggy and an unnecessary app.

---

### Post by fiat1100d on 2007-07-05
Well in fact I actually disabled the Network Manager, since I had to setup another wifi card with options that weren't present in its interface (e.g. restricted WEP authentication), but the problem is there :(

---

