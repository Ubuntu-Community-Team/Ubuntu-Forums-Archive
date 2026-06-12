---
title: "Connecting LAN to get internet"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by hkullana on 2007-10-26
hi,

i installed ubuntu 7.10 on my toshiba L10. Previously, i used xp and in school when i plug the Ethernet cable to my laptop , it connects to the internet (in the TCP/IP properties, everything was automatic). But, after i installed ubuntu it does not connect to the net.   I configure the connection in dhcp and roaming mode but both of them does not help. When i right click the wired internet connection icon in the right top, and click to connection information it shows me that ip, ...etc is 0.0.0.0 . The icon is like it is connected but i cannot open web pages. Please help me, i cannot find a solution in the google. 

thanks,
hkullana

---

### Post by uhlive on 2007-10-26
well the ip being 0.0.0.0 is a bad thing.. try this...


sudo ifconfig eth0 down

then 

sudo ifconfig eth0 up

---

### Post by hkullana on 2007-10-27
it says permission denied

---

