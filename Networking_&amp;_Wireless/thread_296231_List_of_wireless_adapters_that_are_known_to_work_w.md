---
title: "List of wireless adapters that are known to work with Ubuntu?"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by AceRimmer on 2006-11-09
Hello.  Has anyone compiled a list of adapters for wireless networking that are known to work out of the box with Ubuntu?  I'm thinking of switching to a wireless network but I don't want to have a huge hassle of buying and returning network adapters that won't work properly with Ubuntu.  Or do enough work fine as is to make such a think unnecessary?

Thank you.

---

### Post by FrodoB on 2006-11-09
Do not just go buy one assuming that you can make it work in Ubuntu. Research carefully and make sure that you can compile the drivers even before you buy. And for the first try buying from a retailer that takes no question returns is a big plus.

I could recommend a few, but they all require installing source and compiling the driver, which some are not willing to do.

The Netgear WG111 v2 works out of the box with Edgy, but it is no longer in production and hard to find. I got mine off of Ebay. It uses a chipset (rtl8187) that has spotty support in most versions of Linux and if you have to compile it yourself in the future it would be undesirable, in my opinion, as it does not use a normal compile setup using make.

Are you looking for PCI, USB, Mini-PCI, or PC Card wireless devices? Be aware that Atheros USB devices are not supported in madwifi which surprises me and a lot of others.

For PCI and PC Cards the Atheros chipset has good Linux support in most distros, but I have not had the opportunity to try one it in Edgy yet. 

USB would seem like a long lived technology and I am  getting worried about PC Card because the newer low cost PCs don't tend to have PC Card slots, and I am afraid that they will become available in only high end or professional series machines  which are too expensive for me.

---

