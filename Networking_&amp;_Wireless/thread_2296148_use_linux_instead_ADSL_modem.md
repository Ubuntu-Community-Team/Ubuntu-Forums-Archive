---
title: "use linux instead ADSL modem"
date: 2015-09-23
forum: Networking &amp; Wireless
---

### Post by shangol on 2015-09-23
hi
can i use linux as a hardware modem and no need to adsl modem.
use the linux instead of modem,operate as a DSL modem
Thnx

---

### Post by grahammechanical on 2015-09-23
Linux is a computer operating system (software). You will still need hardware or electronics to make the physical connections between computers using the telphone or some other cable system. So, I would say that it is not possible to use Linux (software) as a hardware modem. But that does not mean that a form of embedded Linux may not be running on hardware modems that are on the market.

Perhaps you are thinking of a Linux equivalent of a Winmodem. Also called, a Software Modem or Softmodem. You will still need an electronic hardware board because I doubt if that kind of electronics is built into computer motherboards as standard. Then the question becomes: Is there a Linux driver for a certain brand of softmodem?

[https://en.wikipedia.org/wiki/Softmodem](https://en.wikipedia.org/wiki/Softmodem)

[http://linmodems.org/](http://linmodems.org/)

[http://linmodems.org/#vendor](http://linmodems.org/#vendor)

Regards.

---

### Post by SeijiSensei on 2015-09-23
You would need to install a hardware card with an ADSL interface jack and find software to drive it.  When I searched for that kind of device, NewEgg offered me a [full-featured ADSL modem for $30]("http://www.newegg.com/Product/Product.aspx?Item=N82E16825165003").  I doubt you could spend much less than that building it yourself if you can find the hardware.

---

### Post by shangol on 2015-09-24
Can i attach a minial device not adsl modem to linux thats origin overload on the computer thats running linux 
and use linux computer resource,such as this
[http://www.bonusstore.us/p/56k-V-92-Usb-Softmodem-96121462.html](http://www.bonusstore.us/p/56k-V-92-Usb-Softmodem-96121462.html)
but for ADSL modem not dialup
Thnx a lot

---

### Post by Lars Noodén on 2015-09-24
You might be able to add something like this one and use that with Ubuntu:
[http://www.sangoma.com/products/s518-adsl-modem-board/](http://www.sangoma.com/products/s518-adsl-modem-board/)

There are others if you look around but I do not know the names.  Search around for "ADSL" and "PCI" or the appropriate hardware for your machine.  I use a Traverse Viking card but they are not made any more. 

Most have firmware that can make the device appear as an ethernet device.  However, connoisseurs apparently run their own PPP setup over the modem instead.

---

