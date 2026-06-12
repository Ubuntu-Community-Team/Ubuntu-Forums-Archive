---
title: "Belkin F5D7000 troubles"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by nrogers64 on 2007-01-13
I know it's not good to ask a question that's been asked a thousand times, but I've looked *everywhere* for an answer to my problem and I can't find the solution anywhere! It's pretty frustrating.

I'm one of the standard cases... a Windows user strongly considering switching to Linux. I have very, very little experience with Linux. I installed Ubuntu 6.10 on my old desktop. I put a **Belkin F5D7000** wireless PCI card in and tried to install it.

If I type "ndiswrapper -l" I get:

[FONT="Courier New"]**blkwgdv7 driver installed, hardware present**[/FONT]

If I type "modprobe ndiswrapper" my wireless card's lights do NOT come on.

If I type "iwconfig" I get:

[FONT="Courier New"][B]lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.[/B][/FONT]

If I type "lspci | grep Belkin" I get:

[FONT="Courier New"]**00:09.0 Ethernet controller: Belkin Unknown device 700f (rev 20)**[/FONT]

If I go to the device manager, I see "Unknown (0x700f)". I click on it and it says:

[B]Vendor: Belkin
Device: Unknown (0x700f)
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown[/B]

If I go to System Tools > Networking I see "Wired connection" (which is my 3Com ethernet card) and "Modem connection", no wireless connection.

I've looked at tons of tutorials and I do what they say but nothing seems to work. Any ideas? I would really, really appreciate it. Thanks!

---

### Post by teaker1s on 2007-01-15
while no ndiswrapper expert it is worth making sure you have driver directly from manufacturer of your card/dongle because default ndiswrapper ones are flakey. secondly check the inf file is exactly the same(size) between windows versions as I had one that only worked with 98 version of inf file for some bizarre reason

---

### Post by knghtofwired on 2007-01-16
I'm new to both Ubuntu and these forums, but I am having almost the same problem as nrogers64. I've been looking throughout these forums and around other sites for the better part of a day know, with no luck. When I type "lspci | grep Belkin" I get almost the same results as nrogers:

0000:00:08.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

The only difference there being that I have my card one pci slot above nrogers' card. In all the stuff I've read about Belkin wireless cards, I haven't seen any results similar to what I get until I came to this post.

The major difference between our problems would be that when I type "ndiswrapper -l" it tells me that the driver is present, but it says nothing about the hardware. Does anyone possibly know what's up with this and could maybe help us out? I know I for one would really appreciate it.

---

### Post by neilford on 2007-01-17
I have one of these and I have not quite got it working. There are threads related to this issue which has to do with the RT61 chipset that are in our cards. Search through this group for RT61 and you will find a lot of info including a possible solution for it. As I have said, I haven't quite got mine working yet.

neilford
](*,)

---

### Post by ricperry1 on 2007-01-17
Try the following link.  It may help with this network card.  I just bought one and hope to have it up and running soon.

[http://madwifi.org/wiki/Compatibility#Belkin](http://madwifi.org/wiki/Compatibility#Belkin)

Cheers,

Rich

---

### Post by KreutzenbeckA on 2007-10-05
Hi to all,

just a late posting, but I have still the same problem as nrogers64, I have the same configuration with an additional 3Com 3C980 LAN Card.
I found out that this version of the BELKIN F5D7000 has a Realtek Chipset with a RTL8185L Chip.
The complete description on this chip:
   RTL8185L
   6818551
   L6370

I have already made some tests with the NDISWRAPPER (from the UBUNTU Distribution) and the original BELKIN drivers from the CD - no working configuration. Also using the REALTEK drivers for the 8185 did not work.
In the community, I did not find any information for BELKIN adapters with this chipset.4
The MadWifi has also no supported driver for it.
The problem still exists. Due to the fact there is no sufficient support from BELKIN and nobody get this card working I think to buy another one. 

Cheers

Andreas

---

