---
title: "system lags when wlan (and lan) is disabled"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Arne_M on 2007-07-24
Hi guys!

Always when I boot my laptop with disabled wlan and no lan-cable plugged in (I can disable wlan on some hardware way directly on my laptop) I get pretty high cpu-load at regular time intervals that cause my mouse to lag.

But if I turn wlan on afterwards (or already at boot) I don't get this cpu-load anymore. So I think this has something to do with connecting to a network and not being able to.
If I turn wlan off, after it was on once, I don't get those lags either.

Can some of you guys tell me, what might cause that cpu-load?

It doesn't seem to be a process listed in top or so, because those loads are all very low. (It might of course miss those high loads, when they are shorter than the refresh rate of top) So I think it has to be some kernel module.

I already tried disabling the following services, but they don't seem to cause the problem:
NIS
iflpugd
NFS

I'd really appreciate it, if someone of you could help me, cause I might not always have a wlan to activate to stop the lagging.

Arne


PS: It takes very long at boot setting up network interfaces, if wlan is enabled, but doesn't otherwise.
My wlan-card: Intel® Pro Wireless 3945 802.11a/b/g Mini-PCI Card (for Celeron Processor)

---

