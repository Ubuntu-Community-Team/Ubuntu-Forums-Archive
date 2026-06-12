---
title: "SIOCGIFFLAGS Error"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by Joe Rosenthal on 2007-02-06
Im running Edgy Eft with gnome and I accidently clicked the Network Connection manager icon on the top right corner of the screen (where it says eth0, eth1,etc in a dropdown list) and I accidently typed NETGEAR in that box. I have no device named netgear and now when I try and run the network connection manger i get an SIOCGIFFLAGS error.. I tried editing /etc/network/interfaces but it didnt work.

---

### Post by spd106 on 2007-02-07
Try this: 

Right click on the network applet and choose properties. Now select your interface name using the drop down selection box.

---

### Post by deadowl on 2007-02-09
Hmm, I'm getting this same error, and the Network Manager isn't recognizing that I have a wireless internet device.

Before, I had to get it working using ndiswrapper.

---

