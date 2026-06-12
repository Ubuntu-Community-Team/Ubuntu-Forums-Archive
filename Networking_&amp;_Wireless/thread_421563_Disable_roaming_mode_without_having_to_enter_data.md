---
title: "Disable roaming mode without having to enter data?"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2007-04-24
Under Networking, if you open up the Wireless properties and un-tick Roaming Mode, you are forced to enter network data such as ssid, wep encryption type etc in order to click on 'OK' otherwise it remains grayed out....

Is it possible to disable roaming mode without entering any data? Since I connect to a wpa encrypted network I cannot enter any data in that window, but I want network manager to stop connecting to my neighbors wifi and have a little more patience with my own home wifi network.

---

### Post by bnuytten on 2007-04-24
You may want to have a look at /etc/network/interfaces and man page of iwconfig. You can set up wifi so that it only connects to your own network. I believe that's what you want..

---

