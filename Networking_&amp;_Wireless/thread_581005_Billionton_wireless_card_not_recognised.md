---
title: "Billionton wireless card not recognised"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Stibily on 2007-10-19
Hi.

I have recently installed Ubuntu 7.04 on a friend's Packard Bell EasyNote R4360. All is working fine except for the wireless. It uses a Billionton MIWLRP Wireless LAN MiniPCI Card and ubuntu doesn't want to see it. There is no option to enable 'wireless networking' when i right-click on the network icon so it clearly hasn't detected it.

Am I missing any drivers for this product?

Many thanks.
::Tom

---

### Post by kevdog on 2007-10-19
lspci -nn - identifies card

lshw -C network will show if any drivers are associated with the card

---

