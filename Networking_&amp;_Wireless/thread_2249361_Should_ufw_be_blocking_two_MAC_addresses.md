---
title: "Should ufw be blocking two MAC addresses?"
date: 2014-10-21
forum: Networking &amp; Wireless
---

### Post by haplorrhine on 2014-10-21
They both contain my modem's MAC except the terminating 0 replaced with 1, but the modem MAC is appended with two sections and prepended with six sections, those six being what changed. They matched my laptop's wlan for a couple minutes, comprising 15 of 139 UFW block entries.  The one it usually blocks contains six prepended sections that don't seem to match anything on our network, eth or wlan, although ifconfig on our desktop didn't return an eth0 entry.

---

