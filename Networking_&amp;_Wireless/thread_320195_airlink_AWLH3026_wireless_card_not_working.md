---
title: "airlink AWLH3026 wireless card not working"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by garlic on 2006-12-16
I have airlink AWLH3026 wireless card and it's not working under Ubuntu. I do not find the drivers @ airlink webpage. How do I solve this problem?

---

### Post by Stonecougar on 2007-01-03
I'm having problems with this, too. Been helping my sister set up her rig with 6.10, and she's got one of these cards, with a "t" on the end of the number (Is that like with cars, where adding a bunch of extra letters at the end makes it faster/cooler?) Ubuntu won't even notice it's there. I've also been having trouble with one of the Airlink MIMO XR, model number AWLH5026, on my machine. That one gets acknowledged, but it won't look find a network. 

So yeah. Airlink seems to be a bit sparse in the MadWiFi scene. Any help?

---

### Post by rs3 on 2007-03-06
edit: I picked up an AWLH3026 a couple days ago for $10.  It uses the Ralink RT2561 chipset indeed, and I had absolutely no success in making it work in either Dapper or Edgy.  In Dapper, attempts to configure it via iwconfig resulted in a segfault (using the default rt61 module, I had no luck in getting the Ralink official drivers to work either).  My attempts to use Ndiswrapper seemed promising, but I couldn't get dhclient to talk to my router.  I'd pass on this card.

---

