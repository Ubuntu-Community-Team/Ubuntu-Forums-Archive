---
title: "Belkin wireless adapter is detected but I can't detect wireless networks."
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by El-Doble-O on 2008-04-30
Hello, I am complete newb to Ubuntu. Just installed it yesterday while completely ditching Windows XP. I have a Belkin Wireless N USB Adapter. I think the model is F5D8063, but I'm not completely sure as the writing is very very very tiny. Anyway, the adapter is detected according to command lsusb, which reads:

BUS 005 Device 002: ID 050d:0053 Belkin Components

It turns on and everything but it doesn't do what it's supposed to do, get me on the internet. Help?

---

### Post by dgtldaydrmr on 2008-04-30
This will get you started I think...

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Monicker on 2008-04-30
> **El-Doble-O said:**
> Hello, I am complete newb to Ubuntu. Just installed it yesterday while completely ditching Windows XP. I have a Belkin Wireless N USB Adapter. I think the model is F5D8063, but I'm not completely sure as the writing is very very very tiny. Anyway, the adapter is detected according to command lsusb, which reads:

BUS 005 Device 002: ID 050d:0053 Belkin Components

It turns on and everything but it doesn't do what it's supposed to do, get me on the internet. Help?


That ID seems to point to a F5D7050 card.  Is that the model number?  I can't find anything about a F5D8063 model, even at the Belkin web site.


It would help to know the specific version number for your adapter.  There appear to be at least 4 different versions of it, with different chipsets.  Knowing the chipset will narrow which driver and methods you need to get it working properly.

---

### Post by El-Doble-O on 2008-04-30
I think the model number is F5D8053. According to the model# on the back of the device, it is definitely not a 5070. It's also a wireless N.

---

### Post by dgtldaydrmr on 2008-04-30
[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=372137](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=372137)

---

### Post by Monicker on 2008-04-30
> **El-Doble-O said:**
> I think the model number is F5D8053. According to the model# on the back of the device, it is definitely not a 5070. It's also a wireless N.

That model appears to use a RT2870 chipset.

These instructions might help:

[http://ubuntuforums.org/showthread.php?t=766850&highlight=rt2870]("http://ubuntuforums.org/showthread.php?t=766850")

---

