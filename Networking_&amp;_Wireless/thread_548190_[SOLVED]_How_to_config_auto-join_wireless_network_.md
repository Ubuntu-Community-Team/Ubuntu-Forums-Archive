---
title: "[SOLVED] How to config auto-join wireless network settings?"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by AncientPC on 2007-09-11
I use NetworkManager-Gnome to configure / set wireless network settings.  How do I go about changing some of the settings (i.e. remove certain networks from auto-join, give a network higher priority over the other, etc.)?

---

### Post by Paris Heng on 2007-09-11
Auto-join: I think you can use,*** iwconfig*** to disassociate with the AP MAC address.

> iwconfig (interface) ap (MAC Addr)

---

### Post by kevdog on 2007-09-11
I know what you want to do, however Im not sure if you can make a priority list as you want.  This could be possibly set up through a manual script file, but then that would defeat the purpose of network manager.

---

