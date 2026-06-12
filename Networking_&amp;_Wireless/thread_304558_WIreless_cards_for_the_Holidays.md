---
title: "WIreless cards for the Holidays"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by GNUser on 2006-11-22
Hello all!

As the Season of Gift-giving is rapidly approaching, I have one question.

What one Wireless Card should you give to the linux user in the family?

Please, base the recommendation on the quality of the linux driver,the availability of the hardware, and the ease of set-up.

All suggestions are greatly appreciated.:)

---

### Post by ingo on 2006-11-22
I have a ralink 2500 chipset which ubuntu recognises out of the box. wep and wpa work fine, although you have to fiddle with config files (cut and paste kind of job). Am sure there are other cards though which work better. 

BTW, you after a USB, PCI or pcmcia card?

---

### Post by GNUser on 2006-11-22
I'm looking for a good USB card that could be used both for a desktop, and for a laptop, if need be.

Thanks!

---

### Post by FrodoB on 2006-11-22
For newer USB devices it is hard to find anything that is going to work out of the box. For PCI and PC CARD, Atheros will work out of the box on Dapper and Edgy.

For USB the Belkin F5D7050 ver 3000 has a Ralink rt73 device in it and you can compile drivers on Ubuntu. Here are the instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

Another USB Belkin Device is the F5D7050 ver 4000 which uses the ZyDas zd1211b which has a non-functional drivers in Dapper and Edgy, working instructions are at:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

The F5D7050 ver 3000 is available at Newegg for $19.99 plus shipping:

[http://www.newegg.com/Product/Product.asp?Item=N82E16833314011](http://www.newegg.com/Product/Product.asp?Item=N82E16833314011)

at least that is what it was when I purchased it a few weeks back.

---

### Post by DaveLG on 2006-11-22
If you need/want a PCI card I had good luck with a Belkin F5D7000 card both on SUSE 10.0 and Ubuntu 6.1. The card worked out of the box without ndiswrapper.


Details:

**Belkin Version 5000**
Wireless G
Part #: F5D7000 - P10097-C (This came from sticker on the PC Board)
IC-ID: 4711A-WW4201D (This came from sticker on the PC Board)

Part # F5D7000 (This came from the Box)

My history, well some of it, is at [http://movingtolinux.blogspot.com/2006_04_01_movingtolinux_archive.html](http://movingtolinux.blogspot.com/2006_04_01_movingtolinux_archive.html)

---

### Post by diepruis on 2006-11-23
Just be very careful, as many cards have different versions and also different chipsets. The chipset is the important bit. I would dissuade you from buying anything with an rt61 chipset. I have one of these cards, and the drivers do not support PREEMPT or SMP kernels. PREEMPT and SMP are important for performance (especially on a dual-core / hyperthreading CPU), as such I am dissapointed in Ralink for their poor drivers. Either of these issues also affect some of Ralink's other drivers in the rt* range. Lastly, I would only reccommend buying a USB adapter for a laptop, as these devices have connectivity issues in my personal experience. That might just be stupidity on my part.

---

### Post by FrodoB on 2006-11-23
diepruis;

I concur with your comments. The only Ralink devices that I can recommend at the moment are the rt73 compatible devices, the rt61's and below seem to have stability issues, and freezing upon removal issues as well in my experience.

---

### Post by diepruis on 2006-11-23
> **FrodoB said:**
> The only Ralink devices that I can recommend at the moment are the rt73 compatible devices, the rt61's and below seem to have stability issues, and freezing upon removal issues as well in my experience.

My sister has an rt73 USB device - I got that working on Dapper. I think it needs a driver compilation and installation of firmware, though. It was a long time ago, and I can't remember :)

---

### Post by FrodoB on 2006-11-23
This is the procedure that has worked for others and myself:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by diepruis on 2006-11-23
> **FrodoB said:**
> This is the procedure that has worked for others and myself:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

Thanks, that's more helpful than you know :)

---

