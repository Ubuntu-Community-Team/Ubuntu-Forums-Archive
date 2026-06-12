---
title: "WLAN card that works with Ubuntu?"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by AlliumPorrum on 2007-01-28
Ok, now I have used the whole sunday trying to install my new Belkin F5D7017 PCMCIA WLAN- card, but I just can't make it work. I have tried to install a madwifi driver that maybe supports that card, but that really seems to be impossible task for a Linux newbie like me. :=( I've really had enough of this crap, and I will send that card back to the store tomorrow.

So, could someone please recommend me some PCMCIA WLAN card that would work with Ubuntu without any strange & complex compilation- and installation process? Are there any such cards that would work automatically by just plugging it in? Thank you already!

---

### Post by theoneandonlywheeler on 2007-01-28
Hey

I know that my card does (NETGEAR WG311v2) with a little tweaking, look at my thread:

[http://ubuntuforums.org/showthread.php?t=348243&highlight=wg311v2](http://ubuntuforums.org/showthread.php?t=348243&highlight=wg311v2)

Its really easy.

But whether its still available in the shops is another question.

What about ebay?

There is a list here of cards that are compatable (or not):

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

(Although some may need some tinkering)

---

### Post by chocbar31 on 2007-01-28
> **theoneandonlywheeler said:**
> Hey

I know that my card does (NETGEAR WG311v2) with a little tweaking, look at my thread:

[http://ubuntuforums.org/showthread.php?t=348243&highlight=wg311v2](http://ubuntuforums.org/showthread.php?t=348243&highlight=wg311v2)

Its really easy.

But whether its still available in the shops is another question.

What about ebay?

There is a list here of cards that are compatable (or not):

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

(Although some may need some tinkering)


I agree, Netgear worked well for me. I use an internal Intel mini now and it's great!

---

### Post by AlliumPorrum on 2007-01-29
Thanks for your answers, but that WG311 seems to be PCI- card, and I'm searching for PCMCIA card for my laptop... Does anyone have good options for such a card??

---

### Post by AlliumPorrum on 2007-01-29
Does this silence mean that there really isn't any PCMCIA WLAN cards that are supported by Ubuntu...?

---

### Post by jml on 2007-01-29
I have gotten two PCMCIA cards working in Ubuntu.  The NetGear WG511T and the Cisco Aironet 802.11  a/b/g.  Both cards use the Atheros Chip Set and are recognized out of the box.  Now one thing I would recommend is to not use the default network utility that come with Ubuntu.  I recommend downloading and installing two applications.  Network-Manager and Network-Manager-Gnome.  You should be able to find them with Synaptic, the package management application.  Once these are installed, a small icon will appear in the right upper corner of your screen.  You access the fuctionality by either right clicking or left clicking on the icon.  These applications also support more encryption protocols, (WPA, WPA2.)  Good luck. getting wireless to work well is a real challenge.

Joe

---

