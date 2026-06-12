---
title: "Atheros help"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by noiseordinance on 2008-05-01
Ok, so I posted a thread about what the best wireless card is for Ubuntu, which is aparently tabboo as it got ignored. I'm guessing it's a common question that everyone hates.

I'm trying to do my homework and research it myself and I keep reading about Atheros cards and how they perform really well under Ubuntu, but I can't seem to find an Atheros card. Is it a chipset? When I go to Newegg and type Atheros, nothing comes up. How do I find an Atheros card? Is this a card that will work with XP? I'm trying to ditch my POS Broadcom 1390.

If someone could please help, I'd be much obliged. I'm trying to do my homework here.

(PS - I'm also looking at the Intel 2915ABG as an alternative, but everyone says Atheros beats Intel, yet I can't find an Atheros card for the life of me...)

---

### Post by spd106 on 2008-05-01
The most important link I can give you on wireless in Linux is this one

[http://linuxwireless.org](http://linuxwireless.org)


The best driver for Atheros cards is currently Madwifi, so I suggest that you check out their website at [http://madwifi.org](http://madwifi.org) too.

---

### Post by eanske on 2008-05-01
Atheros is a chipset manufacturer. You'll notice they make chips like the AR5000 series (AR5001, AR5005, etc.) for other manufacturers to use on their usb, pcmcia, pci or mini-pci cards.

Atheros chips do perform very well. I used to have an Intel 2915abg which was giving my router a hard time. Constantly had to reset the thing because downloading would crash the router (something to do with the driver and my router not being able to handle the power saving features). I upgraded to an Atheros AR5005GS and no problems with my router since. Not knocking the Intel though it was a choice between changing the card and changing the router, so I chose. 

If you are looking for a card with an Atheros chip you may want to look at this handy little list I found..

[http://atheros.rapla.net/](http://atheros.rapla.net/)

---

### Post by Ivor01 on 2008-05-01
Atheros is a chipset. My Belkin card uses them.:)

---

### Post by noiseordinance on 2008-05-01
> **eanske said:**
> Atheros is a chipset manufacturer. You'll notice they make chips like the AR5000 series (AR5001, AR5005, etc.) for other manufacturers to use on their usb, pcmcia, pci or mini-pci cards.

Atheros chips do perform very well. I used to have an Intel 2915abg which was giving my router a hard time. Constantly had to reset the thing because downloading would crash the router (something to do with the driver and my router not being able to handle the power saving features). I upgraded to an Atheros AR5005GS and no problems with my router since. Not knocking the Intel though it was a choice between changing the card and changing the router, so I chose. 

If you are looking for a card with an Atheros chip you may want to look at this handy little list I found..

[http://atheros.rapla.net/](http://atheros.rapla.net/)

Which card do you use? What make and model? Does it work in XP?

I'm just dying for a recommendation here. I've been researching this for days and I'm constantly hitting walls left and right. I will pay $20-60 for a good card that works with Ubuntu and XP with no hassle.

---

### Post by noiseordinance on 2008-05-01
This is the type of thing that is confusing the bajesus out of me:

[http://ubuntuforums.org/showthread.php?t=759864](http://ubuntuforums.org/showthread.php?t=759864)

This card is supposed to be supported out of the box, and I almost bought one this morning... yet it too has problems. There should really be a sticky for the #1 PCI-e wireless mini, the #1 PCI wireless, the #1 PCMCIA, etc. This would save a lot of redundant questions and confusion.

---

### Post by Monicker on 2008-05-01
Which form factor do you need?  PCI? PCMCIA? Other?

I have 2 pcmcia cards, with atheros chipsets, which work out of the box with Windows and Ubuntu.

Netgear WG511T
Airlink AWLC4030

---

### Post by noiseordinance on 2008-05-01
I need a solid PCI-e wireless mini card for my Vostro 1500 laptop to replace my Broadcom 1390 wireless mini card.

---

### Post by eanske on 2008-05-01
Here's a card from gigabyte that should do the trick. It has the AR5005GS chip, the same I am using. 
[http://www.giga-byte.com/Products/Communication/Products_Spec.aspx?ProductID=2215&ProductName=GN-WI01GT](http://www.giga-byte.com/Products/Communication/Products_Spec.aspx?ProductID=2215&ProductName=GN-WI01GT)

The madwifi driver works with the AR5005GS. 

As always a handy list to consult is the wireless card supported list, here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

If you are looking for a place that carries the gigabyte card here's one.
[http://www.oxfordtec.com/us/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mP](http://www.oxfordtec.com/us/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mP)

Lastly, I don't think Dell laptops do any Bios checks on the wireless cards, but just to be sure you may want to check with Dell support or do some google-ing to see if this is the case. 

Good luck.

Erik.

---

### Post by noiseordinance on 2008-05-14
I'm just about to buy the super-G minipci Gigabyte card that was mentioned above. I have to ask though, does anyone know much about wireless-N? I know it hasn't been finalized as of right now. However, does that mean that the spec within ROUTERS isn't final, or the spec within ADAPTERS, or both? I'm just trying to see if it's safe to buy a wireless-N adapter at the moment. I don't own a wireless-N router, but will when the time is right. Just trying to avoid buying a new G adapter only to replace it in several months...

This is the card I'm checking out: 

[http://www.oxfordtec.com/us/p125/GIGABYTE-GN-WI06N-802.11N-a/b/g/n-draft-2.0-miniPCI-EXPRESS-wireless--Atheros-AR5008-chipset-AirCruiser-N300-Dual-Band-Mini-Card/product_info.html](http://www.oxfordtec.com/us/p125/GIGABYTE-GN-WI06N-802.11N-a/b/g/n-draft-2.0-miniPCI-EXPRESS-wireless--Atheros-AR5008-chipset-AirCruiser-N300-Dual-Band-Mini-Card/product_info.html)

---

### Post by physeetcosmo on 2009-11-19
> **noiseordinance said:**
> ...I'm guessing it's a common question that everyone hates...

This is a difficult question to answer because there is no "all encompassing answer". The answer is always "it depends".

What do I mean? Well, what do you want to DO with the wireless card? Here's a lot of options to consider:

Do you need to control power consumption?
Do you want to be able to scale data rate?
What 802.11 standards do you want to use?
What kind of encryption do you want to use (server-certificate based or secret key)?
Do you need to control the wireless power output?

And my favorite question:
Do you need to use signal injection?

This is a form of "packet restructuring" where the wireless card can interface with an algorithmic-based application that rewrites packets that are captured.

Obviously this can be abused and I DO NOT RECOMMEND USING THIS KIND OF CARD THIS WAY!!!!!!

Myself, being an Electrical Engineer, I utilize signal injection to test any wireless devices that I am designing/prototyping. It is very useful to test different packet structures and if my device is controlling/responding to them properly.

Hope this helps the original poster or any others.

Good day.    :p

---

