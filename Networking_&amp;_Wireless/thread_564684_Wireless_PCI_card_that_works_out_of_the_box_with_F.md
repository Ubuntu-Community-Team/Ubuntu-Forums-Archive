---
title: "Wireless PCI card that works out of the box with Feisty Fawn"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by peeto on 2007-10-01
I just spent about a week trying to get a no-brand wireless g pci card working on linux. card is realtek 8185l based. tried native driver- no luck. same with rtl-wifi drivers compiled from scratch. tried ndiswrapper with bundled win98, winxp and realtek winxp drivers.  can't find the router with or without wep. ( tried 2 different routers). I want to get a card that will work out of the box, preferably with native drivers ( Not ndiswrapper) any suggestions? 
Thanks

---

### Post by w4ett on 2007-10-02
The out of the box experience has improved quite a bit in Gutsy (hopefully you are considering upgrading)  I use a belkin card and it was automatically supported.

---

### Post by Panthony on 2007-10-02
I got a Linksys (WMP54G) PCI adapter. Down loaded from Linksys site a Ubuntu driver. goog to go. 
:)

---

### Post by kevdog on 2007-10-02
Not sure what gusty brings, but some atheros chipsets work out of the box in feisty -- albeit you need to install the restricted drivers package -- that basically installs the madwifi drivers.  If you check the madwifi site it will tell you the exact chipset numbers that are supported.  Im not sure however if you are looking on line or standing at the store, how exactly you are going to tell the exact Atheros chipset number by looking on the box.  Some research on google and in the forums looking for exact model numbers/version numbers would be necessary

Some ra chipsets are also supported out of the box, however I think this is a little bit more dicier.

---

