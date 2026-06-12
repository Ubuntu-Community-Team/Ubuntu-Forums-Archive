---
title: "DWL G650 (atheros) after kernel upgrade"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by Didius on 2006-12-18
Hi

Recently i've ugraded my kernel, if i want to use my wireless card now (DWL G650 pcmia) my system locks up. (I just tested it with my VPN connection)
After a couple of lockups i checked dmesg and this error shows up:
NETDEV WATCHDOG: ath0: transmit timed out

What happend, how can I fix this?

---

### Post by tturrisi on 2006-12-18
You need to download the madwifi module, build it & compile it into the new kernel.  Or check synaptic if theres a new restricted modules package for the new kernel.

---

