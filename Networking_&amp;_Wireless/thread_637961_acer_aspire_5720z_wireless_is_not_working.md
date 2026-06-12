---
title: "acer aspire 5720z wireless is not working"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by firedragonsf on 2007-12-11
ok there are alot of confusing tutorials on this matter. the matter is that there is no wireless on my computer. could somebody give me a simple easy fix to the problem. preferably a step by step guide. keep it simple and easy to understand (dont use fancy words or abreviations). thx.

---

### Post by ASchweitzer on 2007-12-11
first, which version of ubuntu are you running, and is it 32 bit (X86) or 64 bit?
second, go into terminal (applications > accessories > terminal) and type the following:
```
lspci
```
this lists every piece of hardware attached by PCI slot.

please post any listing that includes "Ethernet controller"
there will most likely be two, one for your LAN adapter, and a second for your wifi adapter

---

### Post by NORpolarbear on 2007-12-12
broadcom corporation netlink BCM5787M GIGABIt ether net pci express
this is what i get when i type lspci into terminal. i have the same computer


we like :popcorn:

---

