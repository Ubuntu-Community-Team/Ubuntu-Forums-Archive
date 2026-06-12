---
title: "RT61 support"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by dandart on 2008-03-22
In Feisty, my D-Link DWL-G510 (rt61) worked perfectly out of the box IF I did the network configuration manually without NetworkManager.

Now in Gutsy, the module 'rt61pci' was loaded, which does not work with this card, where 'rt61' was loaded in Feisty and should have been loaded. This stopped me using Gutsy. I'm still using Feisty, after nearly a year, so I don't have the right software versions. (i'm using backports).

Please ensure Hardy has rt61 instead of rt61pci modules, or a choice made available in installers if the card is detected, or the right choice made out of both modules. Thanks.

The names were:

ra1 (feisty) WORKING
wlan0/wmaster0 (gutsy) NOT WORKING

---

