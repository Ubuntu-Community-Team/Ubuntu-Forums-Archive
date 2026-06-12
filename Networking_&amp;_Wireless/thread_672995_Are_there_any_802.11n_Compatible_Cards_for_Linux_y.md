---
title: "Are there any 802.11n Compatible Cards for Linux yet?"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by bus_ter on 2008-01-20
6 months ago the answer was no. At best a few 802.11n cards could be made to work in 802.11g mode.

Has there been any progress?

Windows has been running this speed for quite a while now :( I always thought Linux was ahead of the game when it came to networking?

Hopefully someone  has some good news?

---

### Post by bus_ter on 2008-01-20
I guess nobody knows?

I'll try again in another 6 months... :popcorn:

---

### Post by funkz on 2008-01-23
Yeah, I would love to know this too.

I am building a new PC and have just bought a _[Belkin Wireless N Router](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=382477)_ (draft 2.0 802.11n) as I also just had ADSL hooked up. It drops to 802.11g when any clients on the network cannot operate in 802.11n. I haven't yet bought a wireless PCI/PCIe adaptor yet as I'm choosing based on how Linux support is for it. I'll be dual-booting Vista/Ubuntu, so am looking at getting an N-compatible PCI/e adaptor so I can make use of the full speed in Vista. Seems there's no solid support for 802.11n adaptors in Linux.

Like bus_ter said, I'd be more than happy with a 802.11n card that operated in 802.11g in Linux? Is this likely? Does anyone know of any 802.11n adaptor cards that would work in Linux, but in 802.11g only (for the time being)?

Maybe my only option is to get a proper 802.11n adaptor (regardless of Linux) for Vista **and** a widely-supported-in-Linux 802.11g adaptor for Ubuntu? Can pick up 802.11g PCI cards pretty cheap (AU$30). Then sometime in the distant future, when Linux drivers for the N-adaptor become available, I can throw out the G-adaptor.

Thanks :)

---

### Post by jclemmons on 2008-01-27
Well, I hope this helps someone as I'm part of the way there.

I just picked up a D-Link DWA-552 (802.11n internal PCI card) and it works in 802.11g mode using the madwifi drivers.  The only kicker is that is doesn't work with the version shipping with Gutsy (9.0.3.2 I believe).  I had to uninstall my restricted-modules package and compile a snapshot of madwifi to get it working.  It seems to be working pretty well so far.  There is also another D-Link adapter for PCI Express X1 slots that I assume is based off the same hardware (DWA-556 is the model number) but I could be wrong on that.  Best Buy is selling the DWA-552 for $60 right now which didn't seem bad to me for an n-based card.

---

