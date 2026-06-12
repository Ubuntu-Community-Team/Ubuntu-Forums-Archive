---
title: "lspci doesnt recognize card."
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by peterx2 on 2008-01-29
I have an Encore enlwi-g2 wifi card that is recognized in ubuntu 7.10 properly as 10ec:8185
Realtek....
this card works fine using ndiswrapper.

But in Ubuntu 8.04 this card is not recognized and comes up as 1319:0801 multimedia controller:forte media

I have tried update-pciids and that doesnt help. 
my question is how does this database find a card? doesnt the card contain vender id and device numbers???
pete

---

### Post by peterx2 on 2008-01-30
More mystery.. I tried Knoppix live on the 8.04 box and it too came up with Forte Media FM801.. Currently I assume the lists are at fault. Another box containing ubuntu 7.1 gets it right and yet another box containing Debian Etch also gets it right..(the Debian box has troubles starting Ndiswrapper on boot up.) in any event.. it is obvious  that lspci must be able to see the card before Ndiswrapper or anything else can be done to mount the card. 

For anyone attempting to go wireless via ebay, it will pay to check the support lists first, it appears that there are several low priced wifi pci cards that would be easier to install.
If anyone would care to comment on the pciids list and the tools that work with it (lspci, update-pciids, setpci..) I would appreciate it.
pete

---

