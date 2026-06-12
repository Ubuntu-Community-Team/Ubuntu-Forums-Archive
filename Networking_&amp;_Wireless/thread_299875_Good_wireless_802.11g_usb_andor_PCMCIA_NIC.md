---
title: "Good wireless 802.11g usb and/or PCMCIA NIC"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by BlackRoseBud on 2006-11-14
Does anyone know of any good 802.11g wireless NICs for either USB or PCMCIA that works right of the box with edgy.  I need something that doesn't need ndiswrapper or require you to even access a terminal.  Something that is completely plug and play.  All you have to do to connect to a network is configure it in Systems>Administration>Networking

Please reply w/ any model that fits this exact description for edgy.

Thanks in advance!\\:D/

---

### Post by FrodoB on 2006-11-14
I have not bought a new one in some time so I don't know the models and versions, but for PCMICA (PC Card) find someting that is labeled Atheros G or Atheros Super G and it is supposed to work out of the box.

---

### Post by FrodoB on 2006-11-14
Here is a likely candidate:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=0](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=0)

The advertizing mentions Atheros G.

The model is mentioned as Linux friendly on a Google search.

There are no guarantees, but if you buy it and it works let us all know.

---

### Post by BlackRoseBud on 2006-11-15
Thanks for the recommendation.  I decided to give the Belkin F5D7010 from WalMart a try.  WORKS SO GREAT!  Plug and Play just like I wanted.  Very stable, no dropped connection, no freezing the computer, no crashing nothing but a solid wireless NIC.  Plus they are conveniently available for $35 at a stores that are 24hrs.

For my desktop I think I'll try the Airlink AWLL3026.  I'll have to special order it though.  It doesn't look like there are very many wireless USB NICs that work, so if that doesn't cut it I'll have to get a wireless PCI card.

Word of advice to all, avoid having to use ndiswrapper, stick w/ devices that supported.  Here's a list ubuntu supported devices: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by FrodoB on 2006-11-15
Great, does it have a version number on it? It should say ver XXXX on the box.  Also can you publish the USB ID from the lsusb command?

$ lsusb

Thanks

---

### Post by BlackRoseBud on 2006-11-22
The Airlink AWLL3026 does not work in Edgy, but I've read it does in previous versions!  The Netgear wg111v2 works out of the  box (No NDISWRAPPER REQUIRED) in Edgy, but not in previous versions.

---

### Post by Duroon on 2006-11-22
> **BlackRoseBud said:**
> 

Word of advice to all, avoid having to use ndiswrapper, stick w/ devices that supported.  Here's a list ubuntu supported devices: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Why avoid the ndiswrapper? I used it to get my thinkpad x40's built in wireless to work. Actually have edubuntu 6.1 running on it and the wireless works great now.

---

### Post by FrodoB on 2006-11-22
ndiswrapper is a wonderful thing in that it allows us to use devices that otherwise would not work, but it is extremely problematic unless you present situation has been dealt with by the ndiswrapper developers and in addition the support provided differs from device to device. 

It seldom compares with a well designed native driver, it only supports Ad-hoc and Master modes of operation, it often cannot support signal quality, noise or some other feature. 

It is quite a bit nicer to just plug in a device that is supported in the kernel like an Atheros or Prism 1,2,3,5,3 device and it just works.

I use ndiswrapper for my Broadcom device in my laptop, someday I hope to replace it with an Atheros, Ralink, or Zydas device.

My personal experience is that ndiswrapper works great about 25% of the time. I have yet to see a new native driver come out that was inferior.

The point is that it would be better if you just inserted the device and it started working, rather than mucking around trying to find an NDIS driver that actually worked with the ndiswrapper bandaid.

---

### Post by BlackRoseBud on 2006-11-25
I've found ndiswrapper has been the cause of system freezes for me in Federo, Redhat, Ubuntu, Debian, & PClinuxOS on several different systems with different wireless NIC cards.  Ndiswrapper is a great tool to have available, but I prefer the stability of using supported devices.

---

