---
title: "surfing via the ubuntu installer cd-rom"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by torst on 2007-03-21
hi, i am a newbie and have booted ubuntu from the installer cd-rom to have a look around, and i find it very nice. but, i can't get out to surf pages on the internet... i have a valid ip-adress via dhcp, and can ping a swedish site called [www.dn.se](www.dn.se) and the ip gets resolved, but when trying to surf the page [www.dn.se](www.dn.se) i get the message "unable to connect". the same message shows when trying to surf [www.google.com](www.google.com) or any other site.
please note that i can also ping another computer on another subnet.

short ifconfig info:
eth0
ip: 16.50.2.222
bcast: 16.50.3.255
mask: 255.255.252.0

i noted up to the right next to the system clock that the network connection was set to lo, i changed this to eth0 and i have run the command sudo ifdown eth0 and then sudo ifdown eth0 and i get the same ip-adress. so, my question is: is it possible to surf the net via the installer cd-rom?

---

