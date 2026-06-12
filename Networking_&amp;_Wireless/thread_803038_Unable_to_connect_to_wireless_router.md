---
title: "Unable to connect to wireless router"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by mcapurro on 2008-05-22
Hi!

I manage myself to configure ndiswrapper in my Acer ASPIRE AS5520-5281 with Ubuntu 8.04. Now I can see all the available networks, but the problem is that I can´t connect to my linksys router. I have WPA2 configured on the router. And there is no message displayed.
Any ideas? I've installed wpasupplicant, but did not make any changes to the network configuration file as I don´t want to hard code my router (I have to use the same notebook regularly in other wi-fi networks)
Is there any log file where I can search for a possible error?

Thanks.

---

### Post by Paris Heng on 2008-05-22
> **mcapurro said:**
> Hi!

I manage myself to configure ndiswrapper in my Acer ASPIRE AS5520-5281 with Ubuntu 8.04. Now I can see all the available networks, but the problem is that I can´t connect to my linksys router. I have WPA2 configured on the router. And there is no message displayed.
Any ideas? I've installed wpasupplicant, but did not make any changes to the network configuration file as I don´t want to hard code my router (I have to use the same notebook regularly in other wi-fi networks)
Is there any log file where I can search for a possible error?

Thanks.

Basically if you have configured right wifi driver, the WPA authentication will be prompt. But for your case you available to scan the networks but unable to associate. This mostly is the driver problems, installation problems, compatibility problems. Now what you can try to troubleshoot are:

1. Configure your router as WEP, and try conenct. 
2. Check what your wifi chips using, try other kind of driver. Check with lspci.

Post here back.

---

### Post by mcapurro on 2008-05-22
It seems that finally something had to be restarted. When I turned on the computer this morning, I was able to connect to both WPA and WPA2 encripted wi-fi networks.
Thanks!

---

### Post by pseudo-random on 2008-05-22
Glad its working now.
As far as logging and wireless errors go, one of the best WPA debugging methods I've found is using wpa_supplicant with the -dd switch for extra verbosity. Here you can see the raw data in the encrypted handshake, it doesn't get much more verbose than that. With a little 802.11 knowledge you can quickly diagnose and identify the exact problem rather than just having windows tell you it 'can't connect'. ;)

---

