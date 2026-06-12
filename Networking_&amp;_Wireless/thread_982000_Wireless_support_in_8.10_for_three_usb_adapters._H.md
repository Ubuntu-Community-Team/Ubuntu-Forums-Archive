---
title: "Wireless support in 8.10 for three usb adapters. Help please!"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by jastonas on 2008-11-14
Can anyone tell me if any of the following usb wireless adapters are plug and play in ubuntu 8.10 ?

Netgear Wireless USB 2.0 Adapter Rangemax
Wireless USB Adapter 54Mbps WL-167G V2
Netgear 54Mbps USB 2.0 (WG111)

Or if you can suggest any other that is plug and play..
price range.. 15-30Euros (12-25Pounds)

Its very important.. i want to buy one for a gift to a friend I am trying to turn him to the dark side of ubuntu... He wants to but has problems with his wireless adaptor... Apparently its super hard to make his work in ubuntu from what i saw in forums.

Thanks

---

### Post by nixscripter on 2008-11-14
The Netgear USB WG111 and the Rangemax should work with ndiswrapper.

The WL-167G V2 should work with the RT2500 driver, which is built in as of Ubuntu 7.10.

Both of these are shoulds, however; your milage may vary. Some people have had trouble, some people have had good luck. My advice would be to try them with a LiveCD if you can get a hold of his machine.

---

### Post by jastonas on 2008-11-14
Since its a desktop computer and the only way to connect to the internet is wi-fi, the usb adaptor needs to be plug and play. Arent there any usb wireless adaptors that are 100% supported by ubuntu?

---

### Post by nixscripter on 2008-11-15
I don't think any device is ever "100% supported", but that's just my opinion. Like I said, they very likely are. If you install the driver, and plug it in, it will detect the interface, and then give you a new connection, plug and play. I would suggest trying them with a Live CD.

---

