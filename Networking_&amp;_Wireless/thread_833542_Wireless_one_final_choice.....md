---
title: "Wireless one final choice...."
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by Cuppa-Chino on 2008-06-18
So here I am posting from Windows.. why you might ask, because I have been on an ongoing wireless saga in Hardy. So these are the choices I have:

I have Asrock P35-Wifi MoBo with an USB RTL8187 wifi module and a Edimax Ralink rt2561/rt61 wireless pci card. either work fine in windows and I have very varied success in Linux with both of them. I use wicd as the network manager, with gnome network manager I had to manually restart ralink based card at every boot.

* gutsy with ralink card worked ok - direct driver
* gutsy did not work with asrock USB module (despite what Phoronix.com claimed with OTB)
* hardy works up to -17 with the ralink but native driver crashed the kernel, I cannot find backports for -17 only -16 & -19 (-18 & -19 kernel do not find my wireless card at all by the way, even with backports installed)


so these are my options as I see it:
a) some one suggest a native driver fix for either card
b) Ndiswrapper with one or the other card

let me know what I should do....

---

