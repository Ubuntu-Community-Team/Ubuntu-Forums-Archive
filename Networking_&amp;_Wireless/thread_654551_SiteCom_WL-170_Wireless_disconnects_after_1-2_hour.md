---
title: "SiteCom WL-170 Wireless disconnects after 1-2 hours"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by Yoeri on 2007-12-31
After 1-2 hours of ineternet usage, my Sitecom PC-Card just stops working.

I use Xubuntu 7.10 on an old Asus A1 laptop. When ejecting en re-inserting the pc-card after the crash, the system just hangs and a manual powerdown is nessecary to get it running again.

Anybody got experience wit WL-170 pc card from Sitecom?

Tx

---

### Post by Yoeri on 2007-12-31
ok, I just found that the WL-170 uses the RT2561 chipset ... apparantly, I'm in for some trouble.

I'll just try to replace the linux drivers with NDiswrapper & Windows drivers, hope the disconnections disappear ...

---

### Post by joesnose on 2008-06-30
sorry to dig up an old thread, but i'm having the same trouble, im using the sitecom wl-170. i have tried it on two laptops running xubuntu hardy heron 8.04, and on both it randomly causes crash. for the most part if i'm just web browsing, it just has random crashes but if i try downloading a torrent or stream large video, i can guarantee a crash. i have'nt tried ndiswrapper as i cant find the .inf file for this card, but was wandering if this would fix the problem and or if there was another fix. is this a known problem with this card/chipset?

---

### Post by joesnose on 2008-07-04
update from me, it seems ndiswrapper fixes the problem, i installed the windows driver yesterday did some downloading, streaming and no crashes yet

---

