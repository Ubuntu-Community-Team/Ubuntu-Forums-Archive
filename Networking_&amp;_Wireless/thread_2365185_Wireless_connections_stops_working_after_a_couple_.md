---
title: "Wireless connections stops working after a couple of hours."
date: 2017-07-03
forum: Networking &amp; Wireless
---

### Post by skyhiro on 2017-07-03
Hi im very new to ubuntu. Just installed 16.04 lts and im having an issue with my wireless usb card. Its a D-link WUA-1340.
It worked very well the moment i plugged it in but disconnects randomly after some hours. I checked for drivers but it says it works out of the box. 
Im using my pc to mine so it gets annoying since im not always there to restart the network manager.
Basically i could wireless connections then at some point they all disapear and dont have any connection anymore.

---

### Post by praseodym on 2017-07-04
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of
```

lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```

---

