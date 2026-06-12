---
title: "Small Drivers Problem"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by DeaDZ_Will on 2009-02-25
Ok, i installed Ndiswrapper,
 all that worked well,
 i downloaded my drivers for my wireless card, 
all that worked well,
 then i installed my drivers and it said about forcing parameters alot (when installing) , I double checked it had installed and it said its sucsesful and already installed.
I added ndis to startup and blacklisted the old driver.

i clicked my wireless button and it diddent come on :\
any ideas what i should do?
i have a Atheros AR5007EG Wireless Network Adapter

please help (:

---

### Post by ubudog on 2009-02-25
Do lspci and look for your wireless card driver there.  Let me know what the results are.

---

### Post by ubudog on 2009-02-25
If all fails, I suggest upgrading to 8.10 and looking for the driver in the restricted drivers.

---

