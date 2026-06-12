---
title: "Motorola support?"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by jasonauslander on 2007-06-10
I am completely new to Linux/Ubuntu. I installed Ubuntu 7.04 yesterday.

Right now, I am trying to connect to a Motorola SBG900 Wireless surfboard modem via a Linksys compact Wireless-G USB adapter (Model: WUSB54GC) The modem does not have any encryption or security activated.

The wireless adapter works, because the modem shows up under detected connections. I click on the access point. It attempted to connect, but failed. It did not give me any reason why. I also tried to manually set up the connection, but that got me nowhere.

I emailed motorola tech support, and the told me that the particular modem does not support Linux, but the manual says it does. A friend of mine did not trust the advice from tech support.

Does anyone have any suggestions?

---

### Post by killphil on 2007-08-27
i use a motorola wireless surfboard sbg1000 and linksys wireless usb gc with debian etch.  you need the ralink rt73 drivers.
try this 
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
i couldn't get the seamonkey drivers to work with etch though so I used the drivers from ralink. grab the drivers from this link, but use the instructions from the first link.
[http://wiki.archlinux.org/index.php/RT73_Wireless](http://wiki.archlinux.org/index.php/RT73_Wireless)
hopefully this helps

---

