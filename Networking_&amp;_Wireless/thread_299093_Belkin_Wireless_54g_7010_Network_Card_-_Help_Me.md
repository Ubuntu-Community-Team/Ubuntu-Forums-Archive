---
title: "Belkin Wireless 54g 7010 Network Card - Help Me"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by HardcoreLinux on 2006-11-13
I am pretty new to Ubuntu and Linux and I have a Belkin 54g 7010 Network Card  that I want to be able to connect to the internet with.  So far I black listed the default drivers, installed ndiswrapper, installed the driver, Installed wifi radar.  When I turn on the computer my wireless card power LED is on but when I am in the desktop though the LED is on I can't connect to wireless nor can I detect any wireless networks.

If anyone has a belkin 54g 7010 802.11b or has installed it on to linux and sees this post would you kindly give me a detailed help of how to install it so it may work.

Oh, I use Dapper Drake Ubuntu.

---

### Post by FrodoB on 2006-11-13
Please supply more details to the group. There are multiple versions of your card using differing chipsets. We need to know the model, the version, and the USB ID or PCI ID of the card in question.

Thanks

---

### Post by HardcoreLinux on 2006-11-14
I am not sure exactly the chipset but I will give you some of the information on the back of the card.  

On the back it says this product is approved as Broadcom BCM94306CB
FCC ID: QDS-BRCM1006

There is a checkmark with N10117 and below it P81547

It is a Belkin 802.11b 32-bit Cardbus with 54g wireless the model number is F5D7010

I have the drivers from this from the CD that came with it. I used Ndiswrapper to install the driver.  I got the hardware present, driver installed yada yada yada.  I also blacklisted old 74XX drivers that come with the system.  The card did turn on but there was no way to wireless networks and I don't think it was even using the radio to find wireless networks.  Hopefully you can help me.

---

### Post by FrodoB on 2006-11-14
Have you looked at the instructions and hardware writeup on the ndiswrapper web site?

---

### Post by Fitzcarraldo on 2006-12-03
I don't know whether it will help you for sure, *HardcoreLinux*, because it depends on the chipset in your card, but see the following post:

[http://ubuntuforums.org/showthread.php?t=272813](http://ubuntuforums.org/showthread.php?t=272813)

---

### Post by the music man on 2006-12-03
> **HardcoreLinux said:**
> I am not sure exactly the chipset but I will give you some of the information on the back of the card.  

On the back it says this product is approved as Broadcom BCM94306CB
FCC ID: QDS-BRCM1006

There is a checkmark with N10117 and below it P81547

It is a Belkin 802.11b 32-bit Cardbus with 54g wireless the model number is F5D7010

I have the drivers from this from the CD that came with it. I used Ndiswrapper to install the driver.  I got the hardware present, driver installed yada yada yada.  I also blacklisted old 74XX drivers that come with the system.  The card did turn on but there was no way to wireless networks and I don't think it was even using the radio to find wireless networks.  Hopefully you can help me.
You need to blacklist the bcm43xx driver. I also read somewhere (but don't remember where) that you may need to copy the bcmwl5.sys file from the CD too, and place it in the same folder where you have the .inf file.

---

