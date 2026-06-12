---
title: "Buying a WiFi card"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by cdot85 on 2005-10-27
I am going to put Breezy on my laptop. I want to buy a wireless card that will be detected during setup, i.e. no work on my part. Which brand should i buy?

---

### Post by janne5011 on 2005-10-27
[QUOTE=cdot85]I am going to put Breezy on my laptop. I want to buy a wireless card that will be detected during setup, i.e. no work on my part. Which brand should i buy?[/QUOTE]

I should say buy the best card you can afford and really want and do some work *if* needed.
theres a app ,ndiswrapper, so you can use all cards and its not so hard fix it:).
avoid cards who runs with  acx_pci drivers, that linux driver is not the very best.....

---

### Post by Quirky on 2005-10-28
I bought a Conceptronic PCMCIA card as the driver is GPL'd and known to work with Linux - i.e no need to hack around with wrappers for Windows drivers. 

The card worked with the latest rt2500 beta drivers (compiled from source) in Hoary and it worked "out the box" in Breezy.  The driver works with WPA as well, no need for wpa_supplicant. I assume other Ralink RT2500 chipsets based wireless 802.11g devices will work as well as this one.

[http://ralink.rapla.net/](http://ralink.rapla.net/)

---

### Post by bionnaki on 2005-10-28
get a linksys wmp54g **version 4** - look closely on the box, it'll say v4 in incredibly small print on one of the sides.

this card is supported & you can use wpa...
all you need to do is modify your interfaces file...

---

### Post by beckyh on 2005-10-28
I can confirm that the Belkin F5D7010 wireless card works with Breezy Ubuntu from startup with no problem, just requires setting up of dhcp, wep key etc.

I have to add though that the same card does NOT work from startup under Breezy Kubuntu.

---

### Post by spd106 on 2005-10-31
I used to have a broadcom based Belkin F5D7010 (rev3) v1 card that needed ndiswrapper to run. Now we have the tools built into the kernel it's quite easy to set up with the windows driver and the ndiswrapper-utils package. The only problem is that it signal strength indicators don't work. 

I recently bought an atheros based D-Link G650 C2 (NB not the + version ). It worked brilliantly, no need for any extra packages. Just set it up and go. It uses the ath_hal module included in breezy and I didn't have any problems with setting it up. I haven't tried it on installation yet, but I see no reason why it wouldn't be detected.

The only thing that annoys me is the constant flashing on/off of the two lights when it's connected.

---

### Post by Yutz on 2005-11-01
I'm a tad off subject, but while people have their attention directed here I figured I solicit a few opinions. I just spent hours configuring a Broadcon based card to jive with Hoary via ndiswrapper. The card performs fine, though I want to find a really great card. I've been browsing the Conexant site, and the news blurbs for the "world radio" prism chipset look great; I can't find out about availability though. I really need a card with an external connector and flexible standards. I'm not looking for an economy card; I am willing to spend a little money to get something versatile and powerful.

---

### Post by daller on 2005-11-01
"D-Link DWL 520+" is cheaper, but does it work without ndiswrapper?

---

