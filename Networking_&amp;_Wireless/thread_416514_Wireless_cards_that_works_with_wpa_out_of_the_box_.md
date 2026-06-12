---
title: "Wireless cards that works with wpa out of the box with 7.04?"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by erq on 2007-04-21
Hi!
I have 7 different wireless cards and none of them seems to work with WPA!

Wich cards have you got to work out of the box with 7.04 and WPA?

---

### Post by disabled_20220313 on 2007-04-21
Hi,

Try searching through the wiki.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

It doesn't look that up-to-date but if a card worked in a previous version of Ubuntu you can be confident it still works in Feisty.

Good luck.

---

### Post by erq on 2007-04-21
The fact that the list in the wiki seems a bit outdated was the reason that I made this post. I cant afford to buy more wireless cards for my laptop! =(

---

### Post by Alacrity on 2007-04-21
erq,

make a short list of your 7 cards...and let's compare

alacrity

---

### Post by Aathos on 2007-04-21
ciaran.mooney,

That is what I thought too, but my Belcan F5D6001 doesn't work in Feisty, when it worked out of the box in Edgy.  If anyone knows how to get it working in Feisty though, that would be great.

Aathos

---

### Post by erq on 2007-04-22
My bad, I "only" have 6 cards...

Alacrity, these are the cards:
Dlink DWL-122
Dlink DWL-G630
Dlink DWL-610
Zyxel G-162
Topcom Skyr@cer PC Card 3011
Linksys WUSB54GC

(Not that it matters, yesterday I ordered a new laptop with builtin WLAN that works in ubuntu.)

---

### Post by rwnz on 2007-04-22
I have a DWL-G650+A H/W ver.:E1 which I recently got working under Xubuntu 6.10 after a lot of work. The Ubuntu 7.04 hype said that Ubuntu 7.04 was far more wireless card friendly than the previous version so I've just loaded Xubuntu 7.04 on to my old laptop and enabled Wireless Networking under Applications-System-Network, and the Act indicator flashes but there is no WPA option - only WEP. This is despite there being some WPA functionality existing according to my search in Synaptic Package Manager. Anyway so much for it all being done for me - I'll now try the method I used for 6.10.

---

### Post by coxy on 2007-04-22
I have an Intel Corporation PRO/Wireless 2200BG that works out of the box with WPA-AES in Ubuntu. It also supports WEP in the text based installer.

---

### Post by rwnz on 2007-04-22
Further to my last post I've been having trouble getting my DWL-G650+A  working on Xubuntu 7.04 with WPA through text based setup so I've just tried it with WEP after changing my wireless router to that encryption option and altering the setup in the Wireless Networking GUI under Applications-System-Network and it works. As Coxy stated that his type of card worked with WPA out of the box I assume that Xubuntu can't do this with the D-Link so it doesn't provide the setup options.

---

### Post by Ynem on 2007-04-22
Hi, I've tested 4 wireless cards on 7.04 so far. NONE of them worked.

two usb adapters: 
actiontech adapter (old)
dlink dwl-g122

and two pcmcia cards:
some chinese card: fast fw54c
dlink dwl-g630 ver E2 using the RT61 chipset

The last card worked for about 6 minutes (could surf the internet) and then the system freeses with these log files:

Apr 21 12:44:29 LaptopYen2 NetworkManager: <information>^IUpdating allowed wireless network lists.
Apr 21 12:44:29 LaptopYen2 NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

Y

---

