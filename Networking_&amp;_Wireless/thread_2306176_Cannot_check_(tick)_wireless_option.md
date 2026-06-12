---
title: "Cannot check (tick) wireless option"
date: 2015-12-12
forum: Networking &amp; Wireless
---

### Post by oygle on 2015-12-12
When I click the network icon, there are 3 modes displayed ..

Wireless  Mobile broadband  Airplane

But only the Airplane mode can be checked (ticked). The Wireless and Mobile broadband modes cannot be enabled. I especialyy need the Wireless mode enabled, so it will scan for a wifi device/s.

This was whilst I had a wired connection active. I then disconnected the wired connection, rebooted, but still can't check that Wireless icon ???

```
$ lspci -nn | grep -i net
```
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)

Found the specifications for that computer at [https://www.asus.com/Motherboards/P5QLD_PRO/specifications/](https://www.asus.com/Motherboards/P5QLD_PRO/specifications/)

Don't see wireless anywhere !!!  LOL

Might try a USB with wireless on it; am sure there is one somewhere.  :)

Well, this was caused by a computer not having wireless, so will mark as solved. :)

---

