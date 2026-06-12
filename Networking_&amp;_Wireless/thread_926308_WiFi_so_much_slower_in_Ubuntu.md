---
title: "WiFi so much slower in Ubuntu"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by antknee869 on 2008-09-21
I have noticed WiFi is much, much slower in Ubuntu than in Vista. I have my ThinkPad (Atheros chipset) set up for a dual boot. I installed WiCD in Ubuntu and made sure WiFi is operating at 54Mbps. 
What could cause this?
Thanks

---

### Post by pytheas22 on 2008-09-21
Do you know the exact chipset model?  If not, what is the output of:
```

lspci -nn
```

If it's a very new card, perhaps madwifi (the Atheros drivers) doesn't support it well yet.  You could always switch to ndiswrapper, which would drive the card using Windows drivers.

---

