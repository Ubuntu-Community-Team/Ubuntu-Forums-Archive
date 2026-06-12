---
title: "Screwed up my WLAN with ssb_sprom trying to rebrand"
date: 2015-05-09
forum: Networking &amp; Wireless
---

### Post by bhosada on 2015-05-09
Guys i did something stupid :(

while attempting to use ssb_sprom to change the subvendor/subproduct id on my wn311b (bcm4329) i changed the product id from 0x4329 to 0x432a and now i cant find ssb_sprom because bcm43 doesnt know the true pciid of the card. it now thinks it's 802.11a/n capable only, @ 5ghz & even picks up SSID's of 5ghz networks, never seen it before, but its unable to connect to anything. Is there anyway I can force b43 to load and see my card for what it really is despite the way system is reporting it. I looked at the supported chart and the id for 432a is untested. I just need a way for it to see its real id.

lspci before:

06:00.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)

lspci now:

06:00.0 Network controller: Broadcom Corporation BCM4321 802.11an Wireless Network Controller [14e4:432a] (rev 01)

---

### Post by bhosada on 2015-05-14
So I guess this card is toast? Guess I'll order a refurb tomorrow and return this one in its place and claim it was defective. Thanks for the help forum.

---

