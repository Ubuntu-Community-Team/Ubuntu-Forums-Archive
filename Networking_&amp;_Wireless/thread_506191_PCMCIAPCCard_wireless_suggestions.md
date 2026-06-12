---
title: "PCMCIA/PCCard wireless suggestions"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by jdunn on 2007-07-21
Being unable to find a working driver for my integrated laptop wireless lan controller, I'm considering a PCCard/pcmcia wireless adapter purchase as an option.  So, what are some good, inexpensive wireless adapters out there?  I'm looking for a card that does for wireless on Linux what the Sound Blaster Live Value does for sound on Linux.  In other words, I need an inexpensive wireless adapter that has adequate features, works well and is easily recognized by most Linux distros (or at least Feisty and all future versions of Kubuntu).

---

### Post by jdunn on 2007-07-21
bump

---

### Post by jdunn on 2007-07-21
Please answer.

---

### Post by Skidpad on 2007-07-21
During my research for a supported card, I found that (among others) Ralink RT25XX-based cards worked well.   I bought an RT2500 PCMCIA card in an ASUS WL-107G chassis.

Here's a link with the RT25XX series cards: [Ralink]("http://ralink.rapla.net/") 

I've also heard Atheros-based cards work well, but I do not have any personal experience with them.

EDIT: make sure you do plenty of searching BEFORE you purchase a card.  If you look on this forum, there are people that have had trouble with the RT25XX cards, but mine works fine, out-of-the-box, with my particular hardware.  

YMMV.  :)

---

### Post by kevdog on 2007-07-22
Many of the ra based cards in Feisty you are forced to do a reinstallation of the serial monkey drivers from scatch.  Also network manager and ra drivers conflict, so the rutilt application is the way to go.

Word of caution -- many of these cards that are supposed to work out of the box -- dont.  They often need tweaking.  So dont fool yourself!

---

### Post by bapoumba on 2007-07-22
Hmm.I have an asus WL-107g PCMCIA that has been working out of the box since breezy up to feisty (ralink chipset).
```
06:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
```

FYI, there is currently a bug in gutsy...
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/118205]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/118205")

---

### Post by dphil61 on 2007-07-22
Im new to Linux and also was looking for a wireless card to that would work with Ubuntu, Fiesty
7.04.   I read on another thread that the D-Link cards work well.  I took a chance and bought one 
yesterday.  It was plug and play!  the model# for the Dlink card is WNA-2330.  The name 
of the card is "rangebooster G notebook adapter".   I didnt have to configure anything to get it to work.  

Frank

---

### Post by jimrz on 2007-07-22
Netgear WG511T (the "T" is importaant) ... uses the atheros 5212 chipset / madwifi driver (included in the restricted modules) and works OTB in feisty ... if you need WPA-PSK you will likely need to update the firmware. this is easily done with downlod from the netgear support site

---

### Post by jdunn on 2007-07-22
Thanks all.  More input is appreciated but right now, the netgear WG511T sounds the most promising based on what I've read in various articles and forums.  I may pick one up tomorrow.

The reason for all this:  I have an Acer Aspire 5100-3357 notebook with integrated wireless.  Feisty tries to load MadWifi drivers for the device but doesn't succeed.  I've also tried aceracpi and ndiswrapper drivers without any success at all.  I can't even identify the 802.11G controller beyond it being made by Atheros (can't get a product name or ID).  I can find no one who's had any luck getting the driver to work on this specific notebook.

---

### Post by NeoTaoistTechnoPagan on 2007-07-22
> **dphil61 said:**
> Im new to Linux and also was looking for a wireless card to that would work with Ubuntu, Fiesty
7.04.   I read on another thread that the D-Link cards work well.  I took a chance and bought one 
yesterday.  It was plug and play!  the model# for the Dlink card is WNA-2330.  The name 
of the card is "rangebooster G notebook adapter".   I didnt have to configure anything to get it to work.  

Frank

Bump this one - I have this card now and I'm at the Ubuntu Live conference. It works just fine. I just inserted the card and rebooted the laptop. All works well - even VPN back to the house in FL.

NTTP

---

### Post by fredj on 2007-07-23
Atheros is a wireless chipset and it is used in many different wireless cards and many people do get these
to work under Ubuntu. So it is really a question of how determined are you? I certainly wouldn't want to pay out
more money for a wireless card when my computer already has one built in.
If you want to make your internal wireless work then start by opening a terminal and typing
sudo lshw -class network
Then post the results here. Also tell us about your wireless network. What sort of security does it use,
WEP or WPA?

---

### Post by jdunn on 2007-07-23
fredj,
I've been doing that and much more for a week.
Buying a wireless card was an option of last resort.  I had at least 3 different threads going in this forum with people suggesting different drivers (madwifi, aceracpi, and ndiswrapper) and install methods.  After a week, I've run out of ideas and so has everyone else who was offering up suggestions.  I can't even determine the product of the Atheros wireless card built into my laptop.

Furthermore, the Atheros driver is not going to work with every Atheros wireless controller.

lshw -C network
WARNING: you should run this program as super-user.
*-network UNCLAIMED
description: Ethernet controller
product: Atheros Communications, Inc.
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
resources: iomemory:54000000-5400ffff irq:19

---

### Post by jdunn on 2007-07-23
I just bought a Netgear WG511T.  It worked perfectly for me outofthebox.  Better than I hoped for.

---

### Post by mkjarema on 2007-07-25
> **dphil61 said:**
> Im new to Linux and also was looking for a wireless card to that would work with Ubuntu, Fiesty
7.04.   I read on another thread that the D-Link cards work well.  I took a chance and bought one 
yesterday.  It was plug and play!  the model# for the Dlink card is WNA-2330.  The name 
of the card is "rangebooster G notebook adapter".   I didnt have to configure anything to get it to work.  

Frank

This one also worked for me.  I am working on a WPA network now, that NEVER worked for me previously WEP or open: but worked in seconds with this card.  H/W Ver.: A1 F/W Ver.: 1.10

I also purchased the WUA-2340 USB adapter (same d-link rangebooster) and my fiesty laptop ***didn't even recognize*** it. (it will be going back to the store) :-) H/W Ver.: A1 F/W Ver.: 1.00

---

### Post by Junglizer on 2007-07-25
One thing to keep in mind, which I've not seen much of in this thread, is the version #. Should be listed on the box and always somewhere on the device its self. The most common problem is that you have a device that is known to work but doesn't, simply b/c it is a newer/older version. Due to changes in manufacturing the chipset on the device changes and this is reflected in which version it is. Example, version 4 of the generic Belkin 802.11g PCMCIA devices use some crap chipset, however version 5 and later use Atheros, which works easy as pie in Linux. (Though this card is hard to find now. Stores like Best Buy, Office Depot, CompUSA, etc.. always push the forefront top end models b/c its "*what you need*.") 802.11b cards haven't even been avalible to purchase in stores like those in the last 2 years, yet we're just pushing the limits of 802.11g now, and this is without everyone knowing its only 20mbps. But... I digress.

---

### Post by mkjarema on 2007-07-25
> **Junglizer said:**
> One thing to keep in mind, which I've not seen much of in this thread, is the version #. Should be listed on the box and always somewhere on the device its self. The most common problem is that you have a device that is known to work but doesn't, simply b/c it is a newer/older version. Due to changes in manufacturing the chipset on the device changes and this is reflected in which version it is. Example, version 4 of the generic Belkin 802.11g PCMCIA devices use some crap chipset, however version 5 and later use Atheros, which works easy as pie in Linux. (Though this card is hard to find now. Stores like Best Buy, Office Depot, CompUSA, etc.. always push the forefront top end models b/c its "*what you need*.") 802.11b cards haven't even been avalible to purchase in stores like those in the last 2 years, yet we're just pushing the limits of 802.11g now, and this is without everyone knowing its only 20mbps. But... I digress.

Excellent point. I never even thought of that....(going to edit my previous post)

---

