---
title: "Syslog Errors IEEE 802.11 element parse failed"
date: 2022-01-24
forum: Networking &amp; Wireless
---

### Post by SteelReserve on 2022-01-24
Running Ubuntu 18.04.6 LTS and connecting to the internet on 5 GHz with an ASUS.  Adapter/driver info is as follows:

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlx04d9f5c6df01
       serial: 04:d9:f5:c6:df:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl88x2bu ip=192.168.1.54 multicast=yes wireless=IEEE 802.11AC



My syslog is filled with hundreds of these messages yet I'm connecting to the internet fine.

[INDENT]Jan 24 18:22:39 pursilane kernel: [24818.200100] RTW: IEEE 802.11 element parse failed (id=12 elen=242 left=119)[/INDENT]
[INDENT]Jan 24 18:22:39 pursilane kernel: [24818.302503] RTW: IEEE 802.11 element parse failed (id=12 elen=242 left=119)[/INDENT]
[INDENT]Jan 24 18:22:39 pursilane kernel: [24818.404907] RTW: IEEE 802.11 element parse failed (id=12 elen=242 left=119)[/INDENT]
[INDENT]Jan 24 18:22:39 pursilane kernel: [24818.507295] RTW: IEEE 802.11 element parse failed (id=12 elen=242 left=119)[/INDENT]
[INDENT]Jan 24 18:22:39 pursilane kernel: [24818.609696] RTW: IEEE 802.11 element parse failed (id=12 elen=242 left=119)[/INDENT]
[INDENT]Jan 24 18:22:39 pursilane kernel: [24818.712125] RTW: IEEE 802.11 element parse failed (id=12 elen=242 left=119)[/INDENT]



Not sure if this is a router or driver issue.  Can't find anything online related to "IEEE 802.11 element parse failed".  Any help is greatly appreciated.  Thank you!

---

