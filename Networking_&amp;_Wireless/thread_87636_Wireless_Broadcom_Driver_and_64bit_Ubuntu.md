---
title: "Wireless Broadcom Driver and 64bit Ubuntu"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by alanhigh on 2005-11-08
I have a Compaq Presario V2000 with..

0000:05:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

I know that the 32bit drivers will work with it(ndiswrapper says driver present,hardware present) but because I'm running 64bit it doens't load properly

I've tried downloading the generic drivers from [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php) but they don't detect my hardware at all.

I really have no idea where to go from here.

---

### Post by mips on 2005-11-09
I see someone over in the AMD64 forum has the eaxct same notebook and got it to work.

[http://ubuntuforums.org/showthread.php?t=84565&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=84565&highlight=Broadcom)
[http://ubuntuforums.org/showthread.php?t=82341&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=82341&highlight=Broadcom)
[http://ubuntuforums.org/showthread.php?t=78356&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=78356&highlight=Broadcom)
[http://ubuntuforums.org/showthread.php?t=78442&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=78442&highlight=Broadcom)

---

### Post by alanhigh on 2005-11-09
Installed ndis drivers:
netbc564        driver present

When I followed any of their instructions, thats what I get.

I have heard of the bcmwl564.inf file insetad of the netbc564 driver, but I can't find the bcm inf file anywhere..

---

