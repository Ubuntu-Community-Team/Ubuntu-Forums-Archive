---
title: "Ibex Network Manager Changes"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by mespinos on 2008-11-10
I have had some problem connecting to my school's WPA enterprise network since I upgraded to Ibex.  

I noticed in the WPA enterprise options, there is no longer a "TKIP" data encryption.  My school's network requires this, and may be a reason it is not working.  

I was able to consistently connect to this network with Hardy.

Is there a way to manually configure this network with the correct encryption type I need?


Thanks,
Andres

---

### Post by mespinos on 2008-11-12
BUMP, anyone know?

---

### Post by superprash2003 on 2008-11-12
yea, try system->preferences-> network connections( or something similar).. there under wireless, you should see your wifi network, there you get advanced options..

---

### Post by mespinos on 2008-11-12
The problem with this is with Ibex's new network manager GUI, there is no option for TKIP data encryption, the connection requires this.  It is a hidden SSID that requires TKIP and PEAP.  

I can't seem to find my WPA_supplicant file to add the manual configuration to, do I have to create this file? 

Thanks,
Andres

---

### Post by mespinos on 2008-11-14
BUMP.. Anyone?

---

### Post by iponeverything on 2008-11-14
right click on NM and go to "edit connections" then go to the wireless tab.
select the network and then go to edit.

---

### Post by mespinos on 2008-11-17
> **iponeverything said:**
> right click on NM and go to "edit connections" then go to the wireless tab.
select the network and then go to edit.

Yes, and this worked in 8.04, but in 8.10 the options for the encryption I need are not available.  

SSID: PAL2.0
Auth: WPA
Encryption: TKIP
Auth: PEAP
MSCHAPv2

I have had no problems in 8.04 connecting.. In 8.10 I have no option for TKIP in the GUI.  Where can I manually configure this?

Please help.. Thanks

---

### Post by mespinos on 2008-11-18
BUMP.. Still no wireless

---

