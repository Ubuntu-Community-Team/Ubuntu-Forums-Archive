---
title: "Fiesty Fawn won't recognize my 2wire wireless card"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by Moleboy on 2007-05-05
Ubuntu won't recognize my 2wire usb card, and I don't know how to get the drivers onto it to get it to be recognized, someone please help.  I have SBC internet, a 2wire internet card, and the actual router is in a different room.

Does anyone have any idea how to install it onto my Ubuntu?

Someone please help soon...

--Moleboy

---

### Post by Floppyjoe on 2007-05-05
First find the chipset for your wireless card:
Open a Terminal by clicking on Application/Accessories/Terminal.
Then for a PCI wireless device enter:
```
lspci
```
or for a USB device enter:
```
lsusb
```
Then search the forums for a tutorial for installing your wirelesscard with the information you collect from these commands.
If your card is pci then look under network controller for the info.
A usb card will give a pciid which you can use to search google or ubuntu forums.

---

### Post by Dorsai on 2007-05-05
I have ATT/SBC dsl also using the 2wire modem and usb wireless lan cards. After a bunch of frustration trying ndiswrapper and some other software I gave up and just bought a wireless card supported natively by Ubuntu. There are millions of ATT/SBC dsl users out there and I find it hard to believe no one has written a 2wire usb driver for Linux but it appears to be so.:( You do not need the 2wire adapter, any wireless card will connect to the 2wire modem.

---

