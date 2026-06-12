---
title: "Connection Problems"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by Strates on 2008-03-26
I am using a ralink wmpgV4.1 and am having connection trouble. I can connect with no problems at all when I first boot my PC but after that I will randomly get disconnected between 45 seconds and about 30 minutes and have to reboot my computer to connect again. I have tried several settings, but none will allow me to solve this problem, any help would be greatly appreciated, and if any further information is needed just ask, I'm new to linux so I'm not sure what will be needed.

---

### Post by Eiríkr on 2008-03-27
First, bear in mind that I'm no networking guru.  I'd recommend you back up anything important before diving in.

I've read elsewhere in this Forum that there are problems with the default Network Manager application in Ubuntu.  Many posters have recommended that folks replace Network Manager with WICD, which is not included in the Ubuntu repositories and thus must be downloaded from [its Sourceforge page]("http://wicd.sourceforge.net/").

Good luck,

Eiríkr

---

### Post by Strates on 2008-03-27
I do appreciate the help, but even after installing WICD I am unable to connect properly. I'm still connecting for a short period of time then being required to reboot. Each time I seem to be hanging up on the acquiring IP part of the connection. I cannot use static ip or DNS. Also it will say it has connected to the network even when using an IP of an entirely different subnet. (IE: it is on 192.168.1.100-150, I can supposedly connect with anything else) However when using a random IP it will not try to contact any other hosts through browsers or pings, instead of hanging it immediately cancels.

---

