---
title: "Any of these wireless devices work in Dapper?"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by jchiso on 2006-09-27
After a recent upgrades I'm finding it difficult to get most of my wireless adapters to work.  My network uses a restricted WEP shared key.  They are as follows:

SMC SMCWCB-G 802.11 b/g cardbus.  Claims to have an Atheros chipset but does not work with either madwifi or Windows drivers via ndiswrapper.  Unable to obtain an IP address.

Hawking Technology HWC54G 802.11 b/g cardbus.  Claims to have an RT2500 chipset.  Downloaded the driver and attemted to use ndiswrapper and Windows driver.  Unable to obtain an IP address.

Netgear WG111 v2 802.11 b/g USB.  Claims to have a Prism chipset.  Not recognized by default and won't connect using ndiswrapper.

If anyone has managed to get any of these adapters working under 6.06 release please share any info you can.

Thanks,

-J.R.

---

### Post by jchiso on 2006-09-28
Okay, the SMC card does work in Dapper... it worked in a system I had not tired before.  However, I cannot determine why it works in this one setup and not in the other two.

---

