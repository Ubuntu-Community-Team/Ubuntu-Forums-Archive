---
title: "How to uninstall drivers?"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by DeRRudi on 2007-04-27
Hi all,

I have a Broadcom 4318 network card. I first i installed a bcm43xx driver. This gave me a 11mb/s connection at max. Then i installed the ndiswrapper. now i can get a 54mb connection.
But everytime when i restart the bcm43xx driver is loaded. if i then do:

rmmod bcm43xx
rmmod ndiswrapper
modprobe ndiswrapper

the ndiswrapper is loaded again. How can i make it load on default??

Greetz Rudi

---

### Post by chili555 on 2007-04-27
```
sudo gedit /etc/modules
```and add the following on its own line:```
ndiswrapper
```Save and close. Then do:```
sudo gedit /etc/modprobe.d/blacklist
```and add the following on its own line:```
blacklist bcm43xx
```Save and close. Reboot and let us know.

---

### Post by DeRRudi on 2007-04-27
THNX!!! that did the trick! :)

---

### Post by deadlines on 2007-04-27
Or if you used a .deb for the bcm43xx drivers, just remove the package and it should no longer load them without having to fiddle with blacklisting.

---

