---
title: "Wireless &quot;b&quot;"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2006-12-06
I'm looking for a recommendation for a solid wireless "B" card, that will support WPA in Ubuntu.

Since the broadband connection in question downloads only 4-5mb/s, a "b" router of 11mbps will be more than plenty. It's also an older motherboard, which isn't supporting pci, wireless "g". 

Thanks for any suggestions!

---

### Post by tturrisi on 2006-12-06
Offhand, I don't know of any B-only cards that do support wpa.  Possibly you may find an older card that has updated windows drivers & chipset flash to add wpa functionality.  Better to just figure out why the g cards don;t work in the computer, pci is pci & the type of card should not matter.

---

### Post by DapperMe17 on 2006-12-06
Thanks for your reply.

I thought pci was pci too, but is is an older p3 HP white box. Unfortunately, both pci wireless cards, Linksys WMP54g V4 & Netgear WG311 V3(both brand new), aren't even recognized as hardware in the device manager & lspci -n. HP's forum suggestion was to try a "b" card. 

Thought I'd try that, or a USB "g" adapter...

???

---

### Post by FrodoB on 2006-12-06
The WG311v3 is supposedly has a Marvell 88w8335 chipset and can be used with ndiswrapper, see this instruction:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

If you want to verify that the instruction will work just run lspci and look for Marvell Libertas chipset.

---

### Post by DapperMe17 on 2006-12-06
Thanks, but no salami...neither PCI card shows up in lspci -n.

---

### Post by FrodoB on 2006-12-06
Amazing, I wonder if a new one will either? Is there one you could borrow to check this before spending money?

---

### Post by DapperMe17 on 2006-12-06
Probably makes more sense to go the rout of a usb, either wusb545g or wusb11.

I know...maybe proprietary issues, maybe pre-2000 mobo...who knows!

---

### Post by FrodoB on 2006-12-06
Here are the USB Devices that I have some experience with:

Belkin F5D7050 ver 3000 has a Ralink rt73 device in it and you can compile drivers on Ubuntu. Here are the instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?h ighlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29")

Another USB Belkin Device is the F5D7050 ver 4000 which uses the ZyDas zd1211b which has a non-functional drivers in Dapper and Edgy, working instructions are at:

[https://help.ubuntu.com/community/Wi...cs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

The F5D7050 ver 3000 is available at Newegg for $19.99 plus shipping at the moment.

[http://www.newegg.com/Product/Produc...82E16833314011]("http://www.newegg.com/Product/Product.asp?Item=N82E16833314011")

at least that is what it was when I purchased it a few weeks back.

Zonet ZEW2500P works out of the box. This device is about $25 at NewEgg:

[http://www.newegg.com/Product/Produc...82E16833130111]("http://www.newegg.com/Product/Product.asp?Item=N82E16833130111")

It does have a slow startup, it takes about 12-15 seconds for the device to start working after a bootup or insertion of the device in Edgy. I suspose it is dowloading and starting firmware.

It uses a Ralink rt2570 series chipset and kernel module.

It works well with WEP, I cannot comment upon WPA as I have not yet tried it.

These USB devices are usually available at Wal-mart and Best Buy in the USA. Pricing is around $36-$45 dollars, but if they are near by you can take them back, at least at Wal-mart.

I also have a WUSB11v4 which uses a ALi M4301c chipset that is only supported by ndiswrapper.  If you want a WUSB11 that work out of the box it needs to be a v2.6.

---

### Post by tturrisi on 2006-12-06
How many pci slots on the mb?  If several, have you tried putting the card into different slots?  I recall issues w/ nics & modems in some mbs in windows where the top slot had issues getting detected properly due to irq sharing. The slot itself could be bad too.  Try installing any spare pci device you have laying around just to see it it gets detected, such as a modem or sound card.  Or yank any pci device from another comp temporarily.

---

### Post by DapperMe17 on 2006-12-06
There's 4 PCI slots. I have shuffled the cards, and the pci slots are all good. Neither wireless "g" card is detected in the other slots.

Beginner's luck I guess!

---

