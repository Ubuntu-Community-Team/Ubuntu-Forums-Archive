---
title: "Wusb11 2.4"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by muted on 2005-11-05
Im having a couple of problems making my wireless linksys WUSB11 2.4 adapter work. So i have tried a couple of things, including the driver from:

[http://at76c503a.berlios.de/](http://at76c503a.berlios.de/)

make, make install and so on...

Now this worked on the older ubuntu, but with 5.1 its kinda tricky


Most guides on here are for the v. 2.6...

Can anyone tell me if they have a V. 2.4 and if so how they got it to work??   Should it btw make any difference at all weather its 2.4 or 2.6??

---

### Post by mirza.k on 2005-11-06
i have tried but it still not work :((
can u tell me step by step :((
when i go to step "make"
ERROR
:((

---

### Post by muted on 2005-11-07
try this

apt-get install build-essential linux-headers-`uname -r


Let me know if you can make it work after you have finished the guide...

---

### Post by muted on 2005-11-08
Alright so I got it working...

Turns out the network name HAD to be "linksys" instead of just some random name... phew, alot of hours just for that... So i guess there isn't any difference between v.2.4 and v.2.6 devices...



Though, when rebooting, i have to deactivate -> activate the device before the net work.. any ideas why??

---

