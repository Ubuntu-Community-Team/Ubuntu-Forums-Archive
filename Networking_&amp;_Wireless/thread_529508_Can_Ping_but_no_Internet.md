---
title: "Can Ping but no Internet ?"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by warnesey333 on 2007-08-19
Hi - I recently installed Ubuntu onto my 64 bit Acer Aspire Laptop.
I have gone through the whole procedure of using ndiswrapper to install the drivers for the wireless broadcom network card.
The card is installed correctly - the network can be seen and is connected to.
However - I can only ping my router and view its homepage.
There is no internet connetion at all.

Anyone able to help or have the same problem?
thanks a lot

---

### Post by Steve1961 on 2007-08-19
Try opening a terminal and typing:

sudo dhclient wlan0

---

### Post by warnesey333 on 2007-08-19
oh my god it works..
you have no idea how much that has helped :)
thanks a lot -.-
 
btw earlier i was trying to use the DHCPDISCOVER but it wasnt working at all
no idea why this has worked -.-
thanks a lot!

---

### Post by Steve1961 on 2007-08-19
You're welcome.

---

