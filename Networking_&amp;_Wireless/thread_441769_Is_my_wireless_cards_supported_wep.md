---
title: "Is my wireless cards supported wep ??"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by bbmak on 2007-05-12
this is my card
Asante AL5410-G 802.11g Wireless Cardbus Adapter Card

Does my card support wep or wap in ubuntu?

How do i really check which card is supported in ubuntu?

---

### Post by chili555 on 2007-05-13
This, evidently, uses the Texas Instruments acx111 chipset, for which there is a module built in to Edgy and Feisty. It should auto-detect and connect, once you tell it the ESSID and encryption details. You can do so easily with Network Manager, or just a little harder manually.

As far as I know, every card I am aware of that was manufactured in the past several years, certainly every card that does 802.11g, does WEP and WPA. I am unaware of any card that supports it that linux cannot configure it.

Here is a Wiki page that lists supported cards.  [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) Most of the readily available cards are listed, but obviously not every card. 

If you plug your card in and do:```
sudo lshw -C network
```you will usually see the chipset listed. Search for it on this forum and a dozen people will have posted the method they used to get it going.

---

### Post by bbmak on 2007-05-14
it's detected, but it cannot connect to the AP.
I am using wep.

I am sure that my ap is working because i have been using the internal network card of my computer and it's connected.

---

### Post by chili555 on 2007-05-15
Are you runninhg Feisty which comes with Network Manager installed by default? Network Manager is *supposed* to used wired if it's available, and not wireless. To know if you wireless is working, you will need to detach the wire and do:```
sudo ifdown eth0
```Now try the wireless.

---

