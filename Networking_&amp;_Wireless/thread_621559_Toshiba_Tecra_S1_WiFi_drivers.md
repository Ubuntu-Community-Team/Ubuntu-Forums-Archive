---
title: "Toshiba Tecra S1 WiFi drivers"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by alex.de on 2007-11-23
Hi, after a fresh install of Gutsy, the only thing that it doesn't detect is my WiFi. I've searched this forum and Google'd and it doesn't help my situation.

As far as I know, I used this driver under Windows:
[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=391942&moid=380605&rpn=PT831U](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=391942&moid=380605&rpn=PT831U)

Is there any way I can install Windows drivers on Ubuntu?

Thanks for your help.

---

### Post by alex.de on 2007-11-23
Alright, it sees my wireless adapter: Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter. How do I install the drivers? I downloaded them from Intel.com but I need to "build" the drivers. Can someone explain me how? Thanks.

---

### Post by alex.de on 2007-11-23
When running dmseg | grep 2100, I get the message that says it connot be initialized. Anyone can help me with this please?

```
alex@laptop:~$ dmesg | grep 2100
[    0.000000] ACPI: SSDT 1FFFAA20, 029A (r1 INSYDE   GV3Ref     2000 INTL 20021002)
[   82.852000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   82.852000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   82.852000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   82.928000] ipw2100: eth1: Error initializing Symbol
[   82.928000] ipw2100: eth1: Error loading microcode: -5
[   82.928000] ipw2100: eth1: Failed to power on the adapter.
[   82.928000] ipw2100: eth1: Failed to start the firmware.
[   82.928000] ipw2100Error calling register_netdev.
[   82.928000] ipw2100: probe of 0000:02:04.0 failed with error -5
```

Thanks.

---

### Post by alex.de on 2007-11-24
I really need help guys =/. Yes I know I'm a "noob".

---

### Post by sjeffrey on 2007-11-26
Hey Alex,

I have the same issue with my Tecra M2.
I tried everything with no success.  Compiled 802.11, ipw2100.  Tried every version of the firmware...

I actually ended up using a PCMCIA card for wireless, but I hope someone will come up with an answer to this.

Good luck!

---

