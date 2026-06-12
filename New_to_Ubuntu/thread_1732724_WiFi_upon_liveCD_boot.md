---
title: "WiFi upon liveCD boot?"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by winston99 on 2011-04-18
Should you be able to connect to the internet wirelessly from the liveCd  or do you have to install first?

Ubuntu 10.4 for power pc
PPC G5 w 10.5 OS x
Apple extreme card to apple airport express to Netgear using WEP

---

### Post by grahammechanical on 2011-04-18
You should be able to make a wireless connection when using a live CD. In fact I have done it both on my home machine and on my sister's laptop. In this way you will discover if the modules or drivers for your wireless adapter are built in to the operating system. If not you will have to install a driver for the adapter after you have installed the OS to hard disc.

Regards.

---

### Post by philinux on 2011-04-18
> **winston99 said:**
> Should you be able to connect to the internet wirelessly from the liveCd  or do you have to install first?

Ubuntu 10.4 for power pc
PPC G5 w 10.5 OS x
Apple extreme card to apple airport express to Netgear using WEP

You might have to connect wired first and then install the correct driver. The notification area should show an icon in this case offering the driver.

---

### Post by winston99 on 2011-04-18
Sounds right I had notification that it wanted to get a broadcom driver for me and I couldn't get it due to no connection.  thanks, I go find long ethernet cable

---

### Post by winston99 on 2011-04-18
> **philinux said:**
> You might have to connect wired first and then install the correct driver. The notification area should show an icon in this case offering the driver.

Could I shutdown ubunta  restart osx ,download driver ,shutdown , restart ubunta and find the driver download and install it?

---

### Post by wep940 on 2011-04-18
Just to expand on what philinux posted:
 
Not all wireless drivers can be included on the LiveCD, as some of these drivers are restricted.  Others may not even have restricted drivers, so on that rare occasion ndiswrapper/ndisgtk might still be indicated (please, ndiswrapper with ndisgtk is not difficult, but exhaust all other options prior to using).

---

### Post by Alan5 on 2011-04-18
deleted by the author

---

### Post by Sef on 2011-04-18
> I hope this helps the debate. However I have a problem. I cannot repeat the connection process as the Wireless pane is empty. I use a netbook running Linpus ( that is fedora ) successfully. Advice would be appreciated.

Please start your own thread on your problem. Thank you.

---

### Post by Leppie on 2011-04-18
> **winston99 said:**
> Could I shutdown ubunta  restart osx ,download driver ,shutdown , restart ubunta and find the driver download and install it?
i'm not sure the hpfs+ drivers are included in the livecd, you might be better off copying the driver to a flash drive to avoid the vicious circle frustrations.

---

