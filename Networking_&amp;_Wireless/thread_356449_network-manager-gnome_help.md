---
title: "network-manager-gnome help"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Ink-Jet on 2007-02-08
I installed ubuntu 6.10 edgy eft a few weeks ago, and haven't been able to access the internet through my wpn511 wireless network card.
Thankfully, i know i don't need ndiswrapper, as i somehow managed to connect to an unsecured network.
After trying the network panels for a while, to no avail, i tried installing network-manager-gnome. I've got all the other dependencies installed, apart from libnll-pre6. I've been searching for it, and i just can't find it.

Am i being really blind or something? I just need the .deb file.

Oh, and hey, i'm new to the forum XD

---

### Post by dannyboy79 on 2007-02-08
FYI, edgy and wg511t was not good out of the box supposedly per this link. [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016)
madwifi fixed this issue around 2/6/07 for the wg511t, Gnome NetworkManager (using wpa_supplicant, using madwifi-ng, using ath_pci).

so maybe this is the issue for your wifi card as well?

---

