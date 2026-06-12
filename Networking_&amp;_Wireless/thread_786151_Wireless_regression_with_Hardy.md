---
title: "Wireless regression with Hardy?"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Onay on 2008-05-07
I don't really know how wireless progress could go backwards, but it's just one of the woes that turns me, as well as a large portion of potential linux users, away from Ubuntu.

Anyway I'm using a usb wireless card (DWL-G132) which works perfectly fine in Gutsy with ndiswrapper-1.49. I compiled it from the source in Gutsy and have had no major problems. However in Hardy, I compiled ndiswrapper-1.52 (latest) from the source and installed the same drivers, but to my misfortune it seems that I cannot connect to any available wireless networks. The Network Manager GUI shows the networks, strength, encryption, etc... but it endlessly tries to connect to the network with no results.

Anyone else have this problem?

---

### Post by giovane_murray on 2008-05-19
I have the same problem using an atheros pci card. I used to connect flawlessly with ndiswrapper 1.45...Wireless in hardy sucks

---

### Post by seantm on 2008-05-19
Another little hardy glitch..

No wireless either. It's basic intelwi-fi card in my T61. It worked seamlessly in Gutsy right out of the box. Now I've upgraded and suddenly no wireless. It sees the card but can not connect. I looked around the forum and tried the following --says it's sleeping...still nothing... Anyone out there with a T-61 who can give me some advice on how to wake it up and connect? TIA.

seantm@techopia:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7e:93:9a:c9
Sending on LPF/ath0/00:19:7e:93:9a:c9
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
seantm@techopia:~$
__________________
Ad astra per aspera!
Registered Linux user #471548
Dual Bootn' Ubuntu Hardy 8.4 & Windoze Vista Hm Basic
ThinkPad T61, 15+", core2duo T7100@1,7GH, 2GB RAM/80HD

---

### Post by Howinlinux on 2008-12-12
I have the same problem with my G132 card!  It took forever to find the answer to get it to work on Gutsy Gibbon, but I finally did. Then I upgraded and it dropped off.  I am going to try to un-install it using NDISWRAPPER and then re-install

I had already tried un-installing it using NDISGTK 'the gui' for NDISWRAPPER, but that did nothing. I am hoping that this will...


Regression is just never good...nor understood :(

---

