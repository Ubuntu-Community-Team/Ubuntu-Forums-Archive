---
title: "Which wifi cards/chipsets WILL work w/ Gutsy"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by carr011 on 2008-01-25
Hi.

I'm done trying to get my Broadcom 4312 to work on my Gateway laptop w/ Gutsy. It was slow w/ Feisty, doesn't connect w/ Gutsy. I've tried so many scripts, ndiswrapper,fwcutter, etc that I'm going to do a fresh install with a different card.

That said, which chipset has the best chance of out-of-the-box success? I've seen the polls about which chipsets are problematic, but those percentages do not reflect the proportion of users for each type of set.  

On my own, I'm looking toward Atheros. However, I really would like to hear from experience before I committ.......Thanks for tolerating such a vague first post! :)

---

### Post by rustybronco on 2008-01-25
pci, pcmcia, usb or?

---

### Post by ugm6hr on 2008-01-25
I agree - Atheros are good.  Check for compatability on madwifi.  My card (works flawlessly with Restricted Drivers out-of-the-box with Gutsy and default Network Manager):

```
08:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

```

Intel wifi cards have open source drivers, and tend to work quite well too.

I'd recommend a mini-PCI card (assuming your laptop currently has an internal mini-PCI that can be swapped out).  Easiest to just search for "wifi mini pci" in ebay.  Something like the TL-WN560G should work OK.
Compatibility info: [http://madwifi.org/wiki/Compatibility/TP-Link#TL-WN560G](http://madwifi.org/wiki/Compatibility/TP-Link#TL-WN560G)

---

