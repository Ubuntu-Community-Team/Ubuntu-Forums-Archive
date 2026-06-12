---
title: "Wireless drops out randomly"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by Yeuclid on 2006-11-07
About 6 months ago, I installed Breezy on a spare PC as an experiment. After some effort I managed to get wireless networking up and running using an ASUS 54g PCI card adapter with NDISWRAPPER, and an appropriate Windows driver.

However, my recent attempts with 6.06, after eventually getting it installed, have been unsuccessful to say the least. This time I am using an 11b USB adapter which is recognised as Prism2 by Ubuntu. I had hopes that this would  get over my previous difficulties with wireless on Badger as it seemed to be a native device. However this was not the case so I eventually uninstalled and blacklisted the Prism drivers and resorted to NdisWrapper with the appropriate XP drivers. After some trial and error, I eventually had a Wlan0, which picked up my Router IP address, and allowed me to access the net.

However, my celebrations were short lived, as after random time intervals the connection drops out. On occasion it can be restarted by unplugging and reinserting the USB adapter, but this happens too frequently for it to be usable.

I've trawled around and seen a few similar stories, so it would seem that all is not well in the world of Wireless Networking with 6.06.

The USB adapter gives a faultless service in XP, so it's not a hardware problem.

It's a bit disappointing that something which works so well in XP should be fraught with difficulties in Ubuntu. This whole area seems to be in need of a general tidy up, as there seem to be too many "loose" addons which don't have any effect whatseover, e.g. wifi-rader and the like. Even the network manager can't report the SSID. Windows wireless zero-config always reports what it finds. Why can't Ubuntu, and why can't it recover a dropped link seamlessly.

Any others out there experiencing these problems?

---

### Post by wieman01 on 2006-11-08
Well... may not be a Linux problem at all. My wireless adapter had issue with in Windows & Ubuntu, however, Windows would reconnect immediately so I would not even notice the connection had dropped. Linux does not reconnect on its own for good reasons (no root authority).

My problem was resolved by changing the router wireless settings. In my case it was the "beacon interval" that I changed from the default (100) to a lower value. After I had done so I have never had a problem since. I recommend that you play around with your router as well & see if it gets any better.

---

### Post by Yeuclid on 2006-11-19
I've since abandoned NDISWRAPPER, and the adapter now works in native mode. Apart from having to manually enable it each time, it works perfectly. I didn't have to do anything to the router.

---

### Post by wieman01 on 2006-11-19
As for manually enabling it, see post #2 of this thread: 

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

