---
title: "USB WG111v2 problems!!!!!!!!!"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by sauny2000 on 2007-04-29
Hi all,

Having a few problems setting up my USB NetGear WG111v2 wireless USB Dongle in Ubuntu Edgy!  I have installed ndiswrapper-common and ndiswrapper-utils 1.8.  I have installed the driver and the output of ndiswrapper -l is:

Installed Drivers:
net111v2 driver installed, hardware present

which is good right?  I then run iwconfig and get told that lo is the only interface available!  wlan0 which is what it was aliased as does not exist!  

Does anyone know what could be going wrong?  Thanks in advance!

Dave

---

### Post by sauny2000 on 2007-05-01
bump

---

### Post by Sensei_V on 2007-05-01
what is the output of the following?
```
iwlist scan
``` and 
```
cat /etc/network/interfaces/
```
and just for fun (although you might want to disguise your IP address for posting on the web)
```
ifconfig
```

---

