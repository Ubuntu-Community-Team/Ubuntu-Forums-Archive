---
title: "Virtualbox breaks Atheros wifi on Toshiba Laptop"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by wbsorsby on 2008-09-11
Virtualbox breaks the Atheros wifi after I connect to the network from XP inside of Virtualbox. The first time it happened I reinstalled the madwifi driver and turned the network connection in Virtualbox manually. Everything worked just fine until I rebooted the laptop. No wifi at that point.

Any ideas on how to solve this problem?

Thanks, in advance.

---

### Post by vegat on 2008-09-18
I've got same situation as this one presented above.
Laptop Toshiba A210, Atheros WiFi card.

---

### Post by mcgoochen on 2008-09-20
same problem for me with MSI VR201. nobody knows what to do ?

---

### Post by vegat on 2008-09-23
I half-solved this problem:

i uninstalled madwifi drivers, downloaded atheros drivers for windows from here: [ftp://ftp.work.acer-euro.com/notebook/extensa_5220/driver/Wireless_Atheros_XB63_v5.3.0.45_XP.zip](ftp://ftp.work.acer-euro.com/notebook/extensa_5220/driver/Wireless_Atheros_XB63_v5.3.0.45_XP.zip) .
Now i'm using ndiswrapper and driver downloaded from above link.

Wifi works even when Virtualbox is running.

I hope this will be helpful for somebody.

---

### Post by megahakujin on 2008-10-10
Ndiswrapper + winxp drivers worked for me as well. (Acer Aspire 5570-2067). THANKS!

---

### Post by jav20a on 2009-05-05
There's no need to use window$ drivers, just uninstall the restricted drivers package and reboot, then wifi will be up...

---

