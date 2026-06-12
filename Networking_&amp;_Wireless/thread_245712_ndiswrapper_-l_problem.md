---
title: "ndiswrapper -l problem"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by cac007 on 2006-08-28
cory@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5. invalid driver!

where can i get a driver?? 

cory@ubuntu:~$ lspci | grep Broadcom\ Corporation
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Titus A Duxass on 2006-08-28
The best place is usually the CD that came with the card.

Failing that do a search, you'll find one.

---

### Post by peliot on 2006-08-28
I just went through that with a broadcom chip. The file is probably called bcmwl5 or 5a but there are many different versions of the files (with different pciids). The only reliable way is to go to the manufacturer website (in my case it was dell) and download the .exe file they provide. Then use the bcmwl5.inf and bcmwl5.sys files after you've unzipped.

When you're on the manufacturer website, it probably identifies the chip with a OEM name rather than the broadcom chip name. In Ubuntu, go to systems->admin-> hardware devices and it will show both the chip name and the OEM name (e.g. Dell TrueMobile 1180).

One other thing to check is that the pciid's are correct. After you install the driver, look at the .conf files in /etc/ndiswrapper/bcmwl5/. The names of those files should correspond to the same pciid that you find if you type "lspci -n" at the command line.

This site is extremely helpful in addition.
[http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/)

Hope that helps,
Philip

---

### Post by haiku99 on 2006-08-28
If you have an windows partition and the card works under windows you can find the drivers there and copy then to your Ubuntu partition...I used an USB flash drive to do this and it worked fine w/ a BCM4311

---

