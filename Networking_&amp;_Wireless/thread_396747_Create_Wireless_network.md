---
title: "Create Wireless network"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Alabaster on 2007-03-29
I run an Edgy machine on a university network which requires me to use static IP to connect to the inter-nets. What I have been trying to do is set up a wireless network so that people can use the connection on my linux box to connect to the internet. I am not a particularly linux savvy and the closest I have come is network-manager, which looked good but wouldn't let me configure my wired connection with a static IP, gateway etc (in fact it didn't seem to let me configure is at ALL).

Various other programs for CONNECTING to a wireless network are out there, but I need one that will let me CREATE one. Wicd looks to be the up-and-comer, but as far as I can tell, it doesn't let the wifi act as an AP.

I realise that wireless networking is something Ubuntu struggles with, but does anyone out there have any idea how I might do this?

Machine stats
Edgy Eft 6.10 x86 version (not 64 bit)
AMD Athlon 64 X2 5200+ Dual Core
ASUS M2N32-SLI Deluxe wireless edition
ASUS 7900 GTX 512 MB
3x Seagate 250 GB SATAII HDD
2GB DDR2-800

Anyone?

---

### Post by Floppyjoe on 2007-03-29
I don't have much help but was just confirming your suspicians that Network-Manager is designed for DHCP.

---

### Post by Alabaster on 2007-04-02
OK, so I've tried network-manager again, and I can manually configure my eth0 connection to use static IP (nwm then ignores that connection). BUT when nwm tries to create a connection....well there is no connection that any of the wireless capable computers we have can detect. Its an ASUS onboard card and as far as I know the drivers should be fine.

Where can I find the configuration files for nwm? Does anyone ahve any ideas about what might be going wrong?

---

