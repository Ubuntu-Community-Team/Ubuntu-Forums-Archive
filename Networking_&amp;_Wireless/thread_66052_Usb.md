---
title: "Usb?"
date: 2005-09-15
forum: Networking &amp; Wireless
---

### Post by darkjedi8359 on 2005-09-15
Since my my marvell yukon network card refuses to operate on linux, is there a way I can bypass the router and use the usb connection on my DSL Router? I'd hate to loose the networked pcs on the router but I would rather have Inet on ubuntu :P.

All I know about the DSL Modem is that the manufacturer is paradyne.

I have searched this forum for USB networking but they all seem to refer to wireless devices. Would I find one of those tutorials and follow similiar steps?

---

### Post by darkjedi8359 on 2005-09-15
Almost working, decided to try and install ubuntu and see what happened.... It detected my eth0 and usb0... On the install it couldn't detect dchp on usb0, and I didn't try eth0..... When it got done installing I ran pppoeconf and set up the DSL connection with usb0.... the connection still didn't work.
Here is the result after trying `sudo pon`> Plugin rp-pppoe.se loaded
RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
pppd: in file /etc/ppp/peers/dsl-provider: nrecognized option usb0Any Ideas?

---

### Post by occy8 on 2005-09-16
have a look here [http://eciadsl.flashtux.org/index.php?lang=en](http://eciadsl.flashtux.org/index.php?lang=en)

your modem is not in their list so you need to find out what kind of chipset is in there

---

