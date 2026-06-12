---
title: "How to:- Belkin F5D7010ea PCMCIA Cardbus Wireless Adapter (Ubuntu 7.10)."
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by yogiman_uk on 2008-03-26
_**Belkin 54g F5D7010ea PCMCIA CardBus Wireless Adapter**_


**Original Problem:-**

Every time I inserted the PCMCIA adapter into my Toshiba Satellite Pro A40 with Ubuntu 7.10 installed the system would lock up.

[B]
Solution:-[/B]


This applies to Ubuntu Gusty Gibbon 7.10 (Released October 2007) / Sorry but I have not tested it with previous releases.

This installation is based on a clean install of Ubuntu.  If you have already messed with ndiswrapper I can't say if it will work or not.

[COLOR="Red"]Before inserting the PCMCIA card......[/COLOR]

You need to extract a couple of the Windows driver files from the original CD.

Make a new folder in your home folder called ndisdriver
[B]
Insert the CD and browse to this location:-[/B]

/driver

and copy bcmwl5.inf and bcmwl5.sys to the ndisdriver folder you created.

Then run Terminal

from the prompt enter the following commands:-

cd ndisdriver

sudo ndiswrapper -i bcm5l.inf

You will be asked for a password for a user with correct privileges

sudo ndiswrapper -l

sudo modprobe ndiswrapper

sudo modprobe -m

 I then rebooted the computer, logged in and gave it a minute to settle down.

Once I had done this I inserted the PCMCIA card and waited a short time at which point the card power light came on and then the network light started to flash. the nm-applet icon on the gnome bar started to flash it's two little blue lights and before long I was connected to my network.

Hope this helps someone, it's taken what seems like a life time to sort this out..... my next task is to get my belkin 54g 7050 USB Wireless adapter working.

Cheers


Yogiman!:)

---

