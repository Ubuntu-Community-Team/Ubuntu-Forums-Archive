---
title: "Trying to get 802.11g &amp; WPA working on laptop"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by adealey on 2007-08-26
I'd like to move one of my laptops to an Ubuntu system (from MS) but can't do it unless I can get 802.11g wireless with WPA-PSK authentication working. I've been trying on-and-off for better than two weeks with no success.

Background: I'm not an idiot nor completely unfamiliar with *nix OSes, though I've never made my living with them day in and day out. I am new to the Linux world (most of my *nix experience has been various BSDs) and to the Ubuntu universe.

The laptop is an old Dell C510 and I have to connect to a Netgear WG302 running in G-only mode with WPA/WPA-2 PSK authentication. The collection of PCCards I have available for the task include:

[INDENT]
D-Link WNA-1330
NetGear WG511v1
NetGEar WG511v2
NetGear WG511T
ZyXEL M-102
[/INDENT]

I currenlly have Feisty on the laptop but would also be more than happy to run Dapper LTS.

I've tried native drivers (for those who have them) and ndiswrappers with no success whatsoever.

If anybody thinks they can walk me through getting one of these (or even some other specific card) to work, I'd be quite grateful. If not, I guess I'm just going to have to conclude that Linux is really, really frustratingly close but still not ready for the desktop yet.

---

### Post by jimrz on 2007-08-26
> **adealey said:**
> I'd like to move one of my laptops to an Ubuntu system (from MS) but can't do it unless I can get 802.11g wireless with WPA-PSK authentication working. I've been trying on-and-off for better than two weeks with no success.

Background: I'm not an idiot nor completely unfamiliar with *nix OSes, though I've never made my living with them day in and day out. I am new to the Linux world (most of my *nix experience has been various BSDs) and to the Ubuntu universe.

The laptop is an old Dell C510 and I have to connect to a Netgear WG302 running in G-only mode with WPA/WPA-2 PSK authentication. The collection of PCCards I have available for the task include:

[INDENT]
D-Link WNA-1330
NetGear WG511v1
NetGEar WG511v2
NetGear WG511T
ZyXEL M-102
[/INDENT]

I currenlly have Feisty on the laptop but would also be more than happy to run Dapper LTS.

I've tried native drivers (for those who have them) and ndiswrappers with no success whatsoever.

If anybody thinks they can walk me through getting one of these (or even some other specific card) to work, I'd be quite grateful. If not, I guess I'm just going to have to conclude that Linux is really, really frustratingly close but still not ready for the desktop yet.

Don't know about the others, but your Netgear WG511T does, in fact,  work "out of box". However if you are still using the original firmware it will not work with WPA (regardless of OS). In order to get this working you need to upgrade your firmware to the latest version available on the Netgear support site.

I have been using this model card with my old laptop since hoary and have had no problems, other than having to update the firmware when I moved to WPA, on any Ubuntu release up to and including gutsy. I, also,  recently installed feisty on an old Inspiron 8000 for a friend, got her a WG511T, upgraded the firmware and it was immediately recognized and functional at install. Additionally, my current laptop, which uses the same Atheros5212 chipset/madwifi driver, has likewise performed without issue since dapper.

---

### Post by adealey on 2007-08-26
Thanks for the response.

I wish that were my experience with the WG511T. I shelled out the money for that card specifically because I found posts saying it worked out of the box. But it doesn't for me. I looked specifically for firmware updates on the Netgear site but all they had were driver & utility updates (both only for Windows). I opened a ticket with Netgear support and their answer was that there are no firmware updates available.

arley

---

### Post by fjpos on 2007-08-29
I'm tying to get WPA  working on my second older laptop (Toshiba Satellite Pro, Feisty 7.04) using netgear`wg511t. The card is working as can pick up my neighbor's wireless who is broadcasting its SSID and perhaps is using WEP. It used to work under windows but I have don't have windows anymore on the laptop. I suspect WPA is the problem but I can't be sure and I am not sure how to proceed. Any ideas?

---

### Post by kevdog on 2007-08-29
Can you post the chipsets of some of these cards.  Im trying to remember, but I havent learned all the model<->chipset relations yet.

---

### Post by adealey on 2007-08-29
Please remind me of the quickest way to determine the chipset for installed hardware. I checked dmesg but I didn't see anything that seemed to identify the chipset.

---

### Post by kevdog on 2007-08-29
If they are pci devices
lspci -nn

If usb devices -- google for them.

---

### Post by adealey on 2007-09-01
Here is what lspci reports about my various 802.11G PCCards' chipsets:

NetGear WG511T: Atheros AR5212
Zyxel M-102: Atheros AR5005VL
DLink WNA-1330: Atheros AR5005G
NetGear WG511v2: Marvell 88w8335 [Libertas]
NetGear WG511v1: Interil ISL3890 [Prism GT/Prism Duette] (this one is probably too old to do WPA)

I have a StarTech card on order which is supposed to use an RA2500 chipset but it won't arrive until Tuesday.

There is also a mini-PCI slot and antenna in this Dell. The best solution would be a mini-PCI card that would work if someone could point me to a source to purchase one.

---

### Post by adealey on 2007-09-04
OK, maybe I'm just an idiot but I think not.

I've now tried with a StarTech CB555WG PCCard which uses a Ralink RT2561/RT61 chip set.

The card is recognized and activated but I still can't connect to the network because I'm only given the opportunity to enter a WEP passphrase, not a WPA passphrase.

Would someone like to enlighten me on what I have to do to make a WPA shared key connection?

(It really shoudn't be this hard, folks).

---

### Post by dodgeman79 on 2007-09-05
I switched from network manager to wicd. I was trying to use WPA myself and network manager is only WEP.  so here is the thread that I used to get and install wicd.

[http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)

---

### Post by adealey on 2007-09-05
Thank you!

Never got the StarTech going (so much for the recommendation of buying a card that uses the ralink chip set) but I was finally able to get the NetGear WG511T going with wicd (although even that took more futzing about than it seems it should have).

arley

---

