---
title: "PCMCIA or USB"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by Demodog on 2007-02-03
Hi!

Is there any wireless PCMCIA-card  or USB-stick that really supports Linux, where the vendor has actually made drivers for it?

Otherwise I would be happy to read suggestions on which to choose?

Im running Edgy Eft btw...

---

### Post by RandomJoe on 2007-02-03
I haven't heard of actual vendor-produced drivers.  But there are a number of drivers out there for various chipsets.

I recently started playing with a PCMCIA card I had lying around and discovered it uses an Atheros chipset, which is supported.  The website [http://madwifi.org](http://madwifi.org) is a wiki for a driver package for this chipset.  There is a supported/compatibility link on the site.  My card is a D-Link DWL-G630.

One note of caution - unfortunately, not _all_ cards of a given model are the same.  Sometimes the chipsets or firmware will change during production, and little if any indication is given.  As an example, my card on the Madwifi site lists a bunch of firmware revisions, not all of which work.

I know it isn't what you asked for, but I have also had success using ndiswrapper to then use a Windows driver.  So far all my cards have worked with that, but they are mostly Broadcom so not a wide range...  The [ndiswrapper wiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page") has a list of working cards and the recommended driver to use.  (Not always the one on the CD provided with the card.)  I couldn't always pick and choose my wireless card (such as whatever was built into my laptop) so I work with what I have.

---

### Post by tturrisi on 2007-02-03
[http://www.data-alliance.net/servlet/the-Wireless-cards%5C-cln--Laptop/Categories](http://www.data-alliance.net/servlet/the-Wireless-cards%5C-cln--Laptop/Categories)

---

### Post by jml on 2007-02-04
Just my two cents worth.  Stick to PCMCIA cards rather than USB devices.  If you search this sub-forum you will find many posts on how difficult it is to get USB devices to work. 

 As for my experience.  Cards based on the Atheros chipset have worked best for me.  The two cards I am currently using With Ubuntu (6.10) and WPA encrypted wireless networks are the Cisco Aironet 802.11 a/b/g wireless card (pricey, but a good preformer,) anf the NetGear WG511T 802.11 b/g wireless card.  Sorry I can't tell you the version number as it is plugged into the laptop I am writing this on.  Oh, one more thing, if you do get one of these cards, do not try to configure it with the network administration application accessed by clicking on System-->Administration;;>Networking.  Use the Combination of network-manager plus network-manager-gnome, which can be downloaded from the repositories if you don't already have it installed.

Joe

---

### Post by tturrisi on 2007-02-04
agrred, don't get usb, get pcmcia. (madwifi does not support usb anyway)
D-Link DWL630G has an atheros chipset, I use one, about 30 bucks.
I also have a Proxim new Orinoco Gold, atheros chipset.

---

