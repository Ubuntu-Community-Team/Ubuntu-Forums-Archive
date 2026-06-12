---
title: "easiest 802.11g pcmcia card ?"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by gdcondor on 2005-07-06
hi !

I'm going to buy a 802.11g pcmcia card but i want to know which one is the easiest to install with ubuntu !
is there one which doesn't require ndiswrapper, recompile the kernel or doing complicated things ??

thanks !

---

### Post by drummer on 2005-07-06
[QUOTE=gdcondor]hi !

I'm going to buy a 802.11g pcmcia card but i want to know which one is the easiest to install with ubuntu !
is there one which doesn't require ndiswrapper, recompile the kernel or doing complicated things ??

thanks ![/QUOTE]
 There's a list of some cards in the wiki here:
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

Generally cards with the Atheros or Prism chipsets work reasonably well out of the box, from what I've read. I'm using the Netgear WG311v2 (this is PCI though) which has the ACX111 chip and it's working well with ndiswrapper with WAP. The native drivers for this card also work (and are already in the kernel) but not yet with WAP.
Hope this helps. ;)

---

### Post by kildare on 2005-07-15
gcondor:

i'm in the same situation as you--but i should warn you, seems like the site listed (which seemed like a good one to me) doesn't seem to always be accurate.  i just bought a netgear wg511t that's listed as working "out of the box"...but after yet another hour and a half wasted time on yet another wireless card, it's going back to the store tomorrow.

---

### Post by tread on 2005-07-15
I would probably go with this:
Proxim/Orinoco  pci a/b/g gold with the Atheros/madwifi.

I have a laptop with integrated atheros, and I know a friend who had a good experience with orinoco.

---

