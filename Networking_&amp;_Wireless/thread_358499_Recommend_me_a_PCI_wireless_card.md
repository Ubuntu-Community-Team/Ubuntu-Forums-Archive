---
title: "Recommend me a PCI wireless card"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by whayong on 2007-02-10
Hello Everyone.  I wanted to get recommendations from everyone and see what the general consensus is on the "easiest" and most compatible wireless card is for Ubuntu 6.10.

I've been struggling with my current wireless card, see this thread [http://www.ubuntuforums.org/showthread.php?t=356439](http://www.ubuntuforums.org/showthread.php?t=356439)

However, I find myself able to justify spending an extra $30 just to relieve the stress and pains of getting my current one to work.  I obviously like Edgy enough to "invest" on it even though it would be SO much easier to go back to XP.

And if possible, recommend me a card that's been proven to work with WPA and Egdy.  I believe it's a miniPCI card.

Here is my system:
Sony VAIO PCG-SRX77
(for reference: [http://www.pcworld.com/article/id,93508-page,1/article.html](http://www.pcworld.com/article/id,93508-page,1/article.html))

Thanks!

---

### Post by FrodoB on 2007-02-11
You want to get an Atheros 108Mbps card like this one:

[http://www.newegg.com/Product/Product.asp?Item=N82E16833127145](http://www.newegg.com/Product/Product.asp?Item=N82E16833127145)

Also note that the mAdWiFi driver that will work out of the box with this device will not support any USB devices for those who are interested.

---

### Post by diablo75 on 2007-02-11
I was going to ask the same question.

So this card will work right away?  Will it JUST WORK?  I bought a cheap USB adapter that would probably work if I knew how to install it and spent hours and hours trying to figure out how.  I don't have that kind of time.  I need a card that just freggin' works.

---

### Post by jml on 2007-02-11
The card FrodoB recommended is a PCI card designed for desk top computers.  Whayong's computer is a laptop.  It requires a "mini pci card"  I am not aware of any mini-pci cards based on the Atheros chip set.  If your laptop has a PCMCIA (aka PC Card) slot then I do have two recommendations for you.  Theseare two cards that are based on the Atheros Chip Set and are compatible with WPA encryption.  First is the NetGear WG511T 802.11 b/g card.  It was recognized out of the box by Ubuntu.  The second card is the Cisco Aironet 802.11 a/b/g card.  It costs more than the NetGear but it has a more powerful transmitter and seems to get better range than the NetGear (I use both.)  

To get WPA working, do not configure with the default network utility.  Download and install network-manager and network-manager-gnome.  Both are in the Ubuntu repository and can be installed via Synaptic.  This application will put an icon in the right upper corner of your screen.  The different features and set up are accessed by either left or right clicking on the icon.  Documentation of this application is spotty at best which is a shame because once it is set up, it works really well.  Post back here if you continue to have problems.  Heck, post back if you succeed and share the details with othe.  :) 

Joe

---

### Post by FrodoB on 2007-02-11
That right, that card will not work, don't ask for a PCI card when you need a PCIe card, they are different things.

---

### Post by whayong on 2007-02-11
Yes, I edited my post immediately after posting since I realized I had to add "miniPCI card."  I however forgot to edit the title as well.  Sorry about that.

Here's a few pages I found since it seems like everyone is asking this question.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[https://www.fsf.org/resources/hw/net/wireless/cards.html](https://www.fsf.org/resources/hw/net/wireless/cards.html)

[http://ralink.rapla.net/](http://ralink.rapla.net/)

I got this one of ebay and will post when I get it installed and *working, hopefully, lol!

[http://www.msicomputer.com/product/p_spec.asp?model=MP54G4&class=com](http://www.msicomputer.com/product/p_spec.asp?model=MP54G4&class=com)

---

### Post by Jozza The Wick on 2008-05-31
I know I posted this elsewhere, but this information can be hard to find, particularly from people who actually have it working. More so for those who think in terms of card model numbers rather than chipsets :D I'm using the Netgear WG511T (mini PCI, for my laptop) under Ubuntu 7.10. Wireless 'just worked' out of the box, and so did WPA (already had it set up on my router, so I just re-enabled on the router & entered the password when prompted, and here I am!)

---

