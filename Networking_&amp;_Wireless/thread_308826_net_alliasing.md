---
title: "net alliasing"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by zooey on 2006-11-28
i have one connection to internet in dormitory and two PC. One have registred mac address and second not. One avice me to do net aliasing i done it how he  adviced me:

ifconfig eth0 down

than from registred PC i copied netmask ip and mac adress andi wrote to the console:

ifconfig eth0:0 netmask 255.255.254.0 hw ether 00:06:C7:B4:G3:H2 10.10.140.130 up

than i connect the lan cable to pc and start firefox but it didn't function

where i made mistake?

---

### Post by taurus on 2006-11-28
Could you please do not double post next time!  I closed the other one in the Beginner Talk then...

---

