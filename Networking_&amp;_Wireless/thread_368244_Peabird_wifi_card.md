---
title: "Peabird wifi card"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by jphil44 on 2007-02-23
Hello, i have a laptop toshiba in wich i install ubuntu Edgy.
I have also a wifi card "Peabird pcmcia".

Yesterday i install ndiswrapper and then i install the correct driver. 
The LED in the card is light up.
and when i try : iwconfig, i see the wlan0 the le wireless car.

This morming i try 
iwconfig and then all interfaces is "no wireless extension". 

Card is ok :
ubuntu:§ lspci
....
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
06:00.0 Ethernet controller: 3Com Corporation 3cCFE575CT CardBus [Cyclone] (rev 10)
....

But 
$ iwconfig
lo        no wireless extensions.
irda0     no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

Can you help me ?

---

