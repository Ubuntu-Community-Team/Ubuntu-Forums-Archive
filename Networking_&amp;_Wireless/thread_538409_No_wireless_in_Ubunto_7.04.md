---
title: "No wireless in Ubunto 7.04"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Overyourhead on 2007-08-30
Hello,

I've installed Ubuntu 7.04. I have working Wireless when I boot from the live CD but I installed it but when I installed Ubuntu. I can not get wireless to work. On the live CD in my network connections I had Moden, wired and wireless. Now with the install I only have Modem and wired connection options. I've followed multiple walk throughs on these forums. I've followed ndiswrapped with the drivers but nothing happens. Any Ideas? I have a Linksys WUSB54g  USB wireless adapter.
Thanks

---

### Post by kevdog on 2007-08-30
You dont know what version of the device you have -- I think there are four.  Im trying to find the chipset of the device.

If you are unsuccessful and getting desperate, boot back into the live cd, get the wireless up and running, and then post the following:
lsmod

---

### Post by Overyourhead on 2007-08-30
I honestly can't tell what version I have. I have looked at every square inch of the device and it doesn't say. I looked in the linksys site and it says to l at the WUSB45G V. ____ but there is no version number after it.

---

### Post by kevdog on 2007-08-30
Im sure you have windows xp drivers for the device.  If you open up the .inf file for the winxp drivers (its a text file) do you see anything that might suggest for example atheros, ra, rt, prism???

---

