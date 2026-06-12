---
title: "Wireless internet advice"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2007-10-12
Hey everyone

I have recently moved into a new house and we have wireless broadband set-up. I have managed to get my wireless internet working using RutilT.

The main problems i am experiencing is that my internet will connect and disconnect quite frequently and just have periods inbetween where it is all ok.

The signal strength is about 40 - 50%.

I just read a how-to about how to get RT2500 wireless cards to work with network manager using ndiswrapper. Now which is the best way to get a pretty reliable wireless connection??

1.) RutilT is the best sort of connection i can expect in linux
2.) Use ndiswrapper since the drivers and network manager will work better
3.) Buy a new wireless card that is compatable with linux

Any help would be great since i will be doing alot of programming and compiling, and have a lot of use with ssh so would love to have it all working quite cleanly.

Below is the info for my wireless card from sudo lspci
```
   
02:07.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```

Matt

---

### Post by scrooge_74 on 2007-10-12
you should try ndiswrapper i think is better developed at this moment.  If you go for a new card look for atheros chipsets or Intel chipsets, stay away of Broadcom

---

