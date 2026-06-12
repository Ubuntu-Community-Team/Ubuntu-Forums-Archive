---
title: "Automatic Network Selection"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by monsieurdozier on 2008-05-20
I live in an apartment complex where there are multiple wireless networks.  When my computer boots up it automatically logs into an unencrypted network "linksys".  How can I get it to automatically log into my encrypted network "Dozier"?  I'm running Ubuntu 7.10.

I tried to do a manual configuration without roaming mode, but it just didn't work.

-monsieurdozier

---

### Post by chili555 on 2008-05-20
I would turn off Roaming and amend my */etc/network/interfaces* similar to this:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Dozier
wireless-key 096c7f280e2bxyzabc
wireless-ap  99:13:19:62:8D:F7
```You can verify the exact ESSID and MAC address with *sudo iwlist eth1 scan*Substitute your interface if it's not eth1.

---

