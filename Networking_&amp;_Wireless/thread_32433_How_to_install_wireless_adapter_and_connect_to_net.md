---
title: "How to install wireless adapter and connect to network?"
date: 2005-05-07
forum: Networking &amp; Wireless
---

### Post by Chris07 on 2005-05-07
How do you install an wireless adapter? Then after that how do you enter the WEP?

---

### Post by enquiry on 2005-05-07
How you install it depends on the chipset (some work out of the box, like Atheros, for example). You access the configuration from System -> Administration -> Networking

---

### Post by az on 2005-05-07
If it is not autodetected, you may have to use ndiswrapper to utilise the windows driver for your device.

You will need to open a terminal and go to the directory where your driver's .inf file is found and then do

sudo ndiswrapper -i (file.inf)
sudo modprobe ndiswrapper
 and then try the graphical network utility again...

If it works, do 
sudo ndiswrapper -m
so that the driver is loaded on boot.

---

### Post by enquiry on 2005-05-07
azz: Is ndiswrapper installed by default?

---

### Post by QuantumCowboy on 2005-05-08
Yes it is installed by default, in /sbin IIRC. 

BTW, I'm getting an "operation not permitted" error when I try to modprobe ndiswrapper, even though I am root....  what might be the problem there?

-QC

hp zv5000, DWL-650+

---

