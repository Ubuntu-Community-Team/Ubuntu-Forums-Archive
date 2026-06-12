---
title: "Dell Inspiron 1525 and a Connexant Modem DR02-D400"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by DellAlva on 2008-11-29
Hallo
I just bought a Dell Laptop Inspiron 1525 and a Connexant Modem DR02-D400. Up to now I could not get access to the internet. Can anyone help me?
I tried:
Menue-driven installation: This allowed me to set a eth0 interface, a provider and a telefonenumber, but can not be activated.

sudo pppoeconf: this found an ethernet maschine but found no responding provider.

sudo wvdialconf: this could not find any modem.

Thanks

---

### Post by caprilo on 2009-04-21
Take a look at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver)

You may download the driver as a Debian package. It should work since Dell sells this model with Ubuntu preinstalled (I have it and use the modem).

---

