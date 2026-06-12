---
title: "64-bit compatible 802.11n NIC?"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2008-10-25
I have a Linksys WUSB300N. It is not supported natively and after a lot of searching it is pretty clear that there are no non-Vista 64-bit drivers for this device. I am getting ready to go back to 32-bit Intrepid Ibex (or Hardy) but I really hate to give up so soon.

Can anyone suggest an 802.11n NIC that is preferably natively supported and if not at least has 64-bit windows drivers that are work with ndiswrapper? Hopefully one that might be available at a local Best Buy or similar. Thanks.

---

### Post by lingenfr on 2008-10-26
A bump a day until the curiosity goes away!

---

### Post by lingenfr on 2008-10-29
Come on, inquiring minds want to know... I know someone out there has a one set up on a 64-bit machine. Share the love, share the knowledge.

---

### Post by Ayuthia on 2008-10-30
Do you know if it is using a Broadcom chipset inside?  It might be possible that the rndis drivers might work. You might check out this link:
[http://ubuntuforums.org/showthread.php?t=847226](http://ubuntuforums.org/showthread.php?t=847226)

It does not seem to have your device, but if it has a 4320 chipset inside, it might work.  If you don't want to compile the drivers for it, you could try and see if it will work in Intrepid since it is running a 2.6.27 kernel so it should have the updated drivers in there.

---

### Post by lingenfr on 2008-10-30
Thanks. The WUSB300N has the Marvel Topdog chipset. I have yet to find working XP 64 drivers for that chipset to try with ndiswrapper. The 32-bit drivers definitely do not work. I am OK with buying a different NIC, but I would like to have some reasonable hope of it working if I spend the money. The Linksys WMP300N looks promising as it has a Broadcom chipset and it seems other may have it working.

---

### Post by Ayuthia on 2008-10-30
> **lingenfr said:**
> Thanks. The WUSB300N has the Marvel Topdog chipset. I have yet to find working XP 64 drivers for that chipset to try with ndiswrapper. The 32-bit drivers definitely do not work. I am OK with buying a different NIC, but I would like to have some reasonable hope of it working if I spend the money. The Linksys WMP300N looks promising as it has a Broadcom chipset and it seems other may have it working.

Here is a link that seems to have the drivers.  I don't know too much about the site because it was something I found through google:
[http://www.station-drivers.com/page/marvell.htm](http://www.station-drivers.com/page/marvell.htm)

It looks like it has an 2000/XP 64-bit driver for the Topdog.  Hope it helps.

---

### Post by lingenfr on 2008-11-01
I tried, unfortunately no joy yet. Those drivers may be the solution, but unfortunately, they come packaged as a setup.exe. I ran it under wine and thought I had the correct inf and associated files, but it didn't work. I expect that someone with an appropriate NIC and XP_64 will have to install the drivers in windows and then grab just the files needed and zip/rar and post them. I don't have XP_64 to try it.

---

### Post by Ayuthia on 2008-11-01
> **lingenfr said:**
> I tried, unfortunately no joy yet. Those drivers may be the solution, but unfortunately, they come packaged as a setup.exe. I ran it under wine and thought I had the correct inf and associated files, but it didn't work. I expect that someone with an appropriate NIC and XP_64 will have to install the drivers in windows and the grab just the files needed and zip/rar and post them. I don't have XP_64 to try it.

Sorry.  I thought that a simple cabextract or unzip would take out the files you need, but I just tried it and it did not work.

---

### Post by lingenfr on 2008-11-08
Bump. Still need help.

---

### Post by RaZoR1394 on 2009-01-02
I have used the Engenius EUB-9701 EXT2 since last year and it has worked very good. It uses the rt2870 Ralink 802.11n chipset and Ralink provides open drivers that work with linux up to 2.6.28.

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

All you need to do is unpack the drivers and run (in the new directory):

sudo make && sudo make install && sudo modprobe rt2870sta. Networkmanager handles the rest. In time linux itself will support the rt2780 chip natively.

[http://www.engeniustech.com/datacom/products/details.aspx?id=233](http://www.engeniustech.com/datacom/products/details.aspx?id=233)

I had a Marvell Topdog NIC myself made by D-Link and it was total and utter ****. I had to run ndiswrapper and the connection failed on my all the time.

I haven't exchanged the antennas on my EUB-9701 EXT2 yet but I may do that.

I have been getting decent speeds with it but It's very dependant on distance, type of router and objects between. Usually I get at least 4MB/s with 15m and a lot of objects and walls between. I also have four routers very close to each other and I think that it may not be very good.

I'm looking at the ESR-9750G router now as Engeniustech has pleased me a lot. It's Gigabit both on the switch and WAN and has 802.11n support with three removable antennas.

The Marvell topdog chipset does from my experience not have support for XP 64bit but however for Vista 64bit.

And there is really no big need for 64bit if you do have PAE support in your system.

---

### Post by lingenfr on 2009-02-15
I bought the Linksys WMP300N (PCI) and it works great in both 32 and 64 bit using the STA driver and the restricted drivers tool. It has produced great results for me in terms of stability and throughput.

---

### Post by bmullan on 2009-02-22
read this...
[http://ubuntuforums.org/showthread.php?t=1071090](http://ubuntuforums.org/showthread.php?t=1071090)

---

