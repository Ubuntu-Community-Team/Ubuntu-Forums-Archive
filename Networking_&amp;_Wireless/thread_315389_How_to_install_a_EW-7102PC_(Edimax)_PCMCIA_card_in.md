---
title: "How to install a EW-7102PC (Edimax) PCMCIA card in Edgy"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by Sandor J. on 2006-12-09
Is there anybody who has experience with this card.
It inserts fine, and lsmod shows me that it uses orinoco drivers.
After reading several threads on this forum and checking the drivers from the Edimax site I suspect the card to be a PRISM driver related.
But blacklisting the orinoco drivers make  my laptop crash during boot (with the card inserted). It boots fine when I insert the card after boot.
modprobe-ing prism_plx after boot loads the driver, but shows no wireless card in the network settings.
Anybody any experience with this??
Would shurely be appriciated

---

