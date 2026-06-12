---
title: "Wireless Recommendation?"
date: 2005-11-10
forum: Networking &amp; Wireless
---

### Post by mark on 2005-11-10
I'm thinking about pickup a PCMCIA wireless network adapter for my laptop.  I've been through the hardware listings on the Ubuntu support wiki but I'm still confused<g>.  Has anybody got a recommendation for such a card that "just works"?  I'm running 5.10 on my Sony VAIO PCG-GRZ610 and I'd prefer native support as opposed to ndiswrapper.

*Thanks!*

Mark

---

### Post by slux on 2005-11-10
I'd recommend a card based on the Ralink RT2500. There is a driver available under the GPL based on the chipset manufacturer's original driver source and I've heard nothing but positive things about it. I also personally have a machine that uses a PCI card with the same chip.

Awesome support although last I checked it wasn't in the main kernel tree yet. At least A-Link has an USB, PCMCIA and PCI version for a very low price available but I don't know how widespread they are outside Finland.

[http://rt2x00.serialmonkey.com/wiki/](http://rt2x00.serialmonkey.com/wiki/)

---

### Post by joeljkp on 2005-11-10
I was about to post this exact question when I saw this thread.

The RT2500 looks good, but I'd prefer something currently stable, proven, and in the kernel tree. Any recommendations?

---

### Post by slux on 2005-11-11
Well, If you're ready to accept 802.11b you have options but as far as 802.11g goes I don't think there's anything satisfying those requirements.

However, in my personal experience the rt2500-based PCI-card has been performing flawlessly for the last 172 days straight (that's the uptime on the headless machine I have connected thru it) so as far as I'm concerned this is indeed stable and proven even though it's not yet in the kernel tree which of course would be a big plus.

---

### Post by spd106 on 2005-11-11
I you can find an atheros based card, they usually work great and have madwifi drivers.

I have a d-link G650 (NOT G650+) and had no trouble... yet. I passed on my old broadcom card to a windows user.

The wiki has a [list]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards"). But it's a bit patchy, most of the entries refer to Hoary.

The best advice is to find someone you can borrow off to test.

Good Luck

---

### Post by Agent86 on 2005-11-12
According to this thread on their forums,

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=398](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=398)

the RT2500 drivers included in Breezy are the latest ones from the Open Source project at serialmonkey.

Breezy and my PCI RT2500 card have been working extremely well together, WPA and all.

---

### Post by slux on 2005-11-12
Neither is yet in the main kernel tree though and madwifi is unlikely to make it in there any time soon as they insist on keeping a part of the driver closed. I understand OpenBSD is working on a free replacement for the part though.

---

