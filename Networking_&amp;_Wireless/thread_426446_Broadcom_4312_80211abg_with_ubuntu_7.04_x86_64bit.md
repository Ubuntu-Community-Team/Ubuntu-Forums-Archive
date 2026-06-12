---
title: "Broadcom 4312 80211a/b/g with ubuntu 7.04 x86 64bit"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by geo_saleh on 2007-04-28
hello guys.

I have small problem with my wireless.

I hope find solution here.

I install ubuntu 7.04 x86 64-bit on my laptop hp dv6284eu

every thing work's except wireless card.

my wireless card is Broadcom 4312 80211a/b/g.

[see this link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom")

its not supported.

what can I do with it.

thanks.

---

### Post by geo_saleh on 2007-04-29
Up

Up


Up

---

### Post by geo_saleh on 2007-04-30
can any one help me

I found this patch but I don't know what to do

bcm43xx_phy.c
```
--- linux-2.6.orig/drivers/net/wireless/bcm43xx/bcm43xx_phy.c
+++ linux-2.6/drivers/net/wireless/bcm43xx/bcm43xx_phy.c
@@ -1225,7 +1225,7 @@ static void bcm43xx_phy_initg(struct bcm
       }
       if (phy->rev < 3 && phy->connected)
               bcm43xx_phy_write(bcm, 0x047E, 0x0078);
- if (phy->rev >= 6 && phy->rev <= 8) {
+ if (phy->rev >= 6 && phy->rev < 8) {
               bcm43xx_phy_write(bcm, 0x0801, bcm43xx_phy_read(bcm, 0x0801) | 0x0080);
               bcm43xx_phy_write(bcm, 0x043E, bcm43xx_phy_read(bcm, 0x043E) | 0x0004);
       }
```

my card is 4312

---

### Post by geo_saleh on 2007-05-05
up

up


up

---

