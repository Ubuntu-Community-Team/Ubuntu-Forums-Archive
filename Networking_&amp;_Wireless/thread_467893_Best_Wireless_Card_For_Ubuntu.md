---
title: "Best Wireless Card For Ubuntu"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by odista on 2007-06-08
I'm looking for a good wireless card for Ubuntu.  I would strongly prefer one that will work out of the box with minimal configuration.  Any suggestions?  Thanks.

---

### Post by dardack on 2007-06-08
Pcmcia? Usb? Pci?

EDIT:
Forgot to say my experience.

I have a PCI BestBuy brand (not called BestBuy but it is their generic brand) that works right out of box.  I shut down ubuntu rebooted and it was there and connected to the network no problems.  (My one issue seems to be that network drops on me quiet frequently but not just with that card).

I also have USB Linksys WUSB11 v2.8 that works right out of box. (Same issues)

---

### Post by SkyScrap on 2007-06-08
I've also today started to research for that kind of information. My current result is here:
[http://ubuntuforums.org/showthread.php?t=467786](http://ubuntuforums.org/showthread.php?t=467786)

---

### Post by thor111 on 2007-06-08
I found this article VERY helpful for a noob like me, and I used it to install my wireless card a few days ago.  It steps through EACH process, and lets you know what you should see.  BTW the TrendNet card I installed is working very well, and it was fairly cheap.

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Hope this helps.

---

### Post by dmoney on 2007-06-08
> **dardack said:**
> Pcmcia? Usb? Pci?


Yeah. Are you on a laptop or desktop? If you want something that's going to work out-of-box with little configuration, go with something with an Atheros chipset. If it's for your desktop, the D-Link WDA-2320 is a good choice. [http://www.newegg.com/Product/Product.aspx?Item=N82E16833127075](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127075)
Best Buy also carries this card if you just want to run to the store and pick one up. 

Here's a list of cards and how well they're supported: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I would avoid anything that requires ndiswrapper to set it up. Not that there are any usability issues - I had to use it to get my PC card on my laptop working - but it's a bit of extra work that's unnecessary if you find the right card. Anything listed with an Atheros chipset should automatically be installed by Ubuntu...all you'll need to do is plug it in, boot up, and find your network and log in and you're set.

---

### Post by zaidee on 2007-06-19
Can anyone tell me where I can buy either of these cards from the uk. I have searched but cannot find anywhere
Am desperate to get my wireless network up and running

---

