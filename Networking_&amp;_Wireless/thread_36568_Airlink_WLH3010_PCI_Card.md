---
title: "Airlink WLH3010 PCI Card"
date: 2005-05-23
forum: Networking &amp; Wireless
---

### Post by malachakla on 2005-05-23
Hello,
I've switched from my troublesome USB adapter to this PCI card now, and I was wondering if anyone can talk me through setting it up.
Which drivers are best?
Do I use the drivers from the CD that came with the card, or since the card is based on the Broadcom chipset should I use others?
Thanks very much!

---

### Post by anders.ostling on 2005-05-24
Hi

Bad news: The WHL3010 PCI/MiniPCI/PC-Card contains a broadcom chip that is not natively supported by Linux. All accordining [http://linux_wless.passys.nl/](http://linux_wless.passys.nl/)

Good news: You can probably use ndiswrapper with the native windows driver. Go to 
[http://ndiswrapper.sourceforge.net/phpwiki/index.php/](http://ndiswrapper.sourceforge.net/phpwiki/index.php/) for much more info than I can give you here.

Good luck. Reply here if there is anything else that you need to ask about.

Anders

---

### Post by kleeman on 2005-05-24
There are a bunch of helpful ndiswrapper howtos in the tips and howtos hoary subforum....

---

### Post by malachakla on 2005-05-24
Yeah, I've tried with ndiswrapper several times with various drivers, and with every driver the wireless card couldn't connect to the network and couldn't even scan for channels of wireless networks.
I'm considering switching back to my original USB Wlan dongle because it's more supported.
Thanks!

---

