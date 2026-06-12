---
title: "Help with wireless card - ndiswrapper"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by telovoyagarcar on 2007-02-04
Ok..
i have this fresh install of ubuntu edgy.
Installed from the alternate cd.
During the installation, i did not have the wireless card plugged into the pcmcia slot, but the installer set a Broadcom controller and asked me for the IP and all the stuff for that interface anyway.
So now, if i type iwconfig, i have it listed as eth1.
I guess i need to remove it and i dont know how.
Then i followed this guide [http://antonym.org/node/89](http://antonym.org/node/89) to install ndiswrapper and my Linksys wpc54g wireless card.
The driver installed fine, but i dont know how to make ubuntu load this card and make it work.

if i type lspci i get these at the end of the list:

02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface


So there you can see.. first the non existent BCM4306 802.11b/g Wireless LAN Controller which looks like it is being loaded as a valid hardware device, and then the Texas Instruments one that i think must be the way ndiswrapper is listing my Linksys card.

so the question is.
How do i uninstall the one that does not exist and how to make work my Linksys card?

Thanks

---

### Post by Metaljaz on 2007-02-04
Read thru this thread to make sure you have things right:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

---

