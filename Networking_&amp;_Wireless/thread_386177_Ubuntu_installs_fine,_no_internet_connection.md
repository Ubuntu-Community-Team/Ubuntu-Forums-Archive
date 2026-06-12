---
title: "Ubuntu installs fine, no internet connection"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by eugenelvhen on 2007-03-16
I installed the latest stable Ubuntu for my grandmother on a 3 year old PC. 
The PC is connected directly to a cable modem. In Windows XP there is a dialer/connection program that needs to be run after you login. 

Ubuntu installs fine, but naturally there's no interent connection at all.
What info do I need to find out from the ISP and what do I do in Ubuntu to make it work?

Thanks.

---

### Post by johnc4510 on 2007-03-16
Open: System>Administration>Networking
Password needed
Make sure the wired connection for cable modem is enabled

---

### Post by eugenelvhen on 2007-03-16
Basically I just have an IP and password that I entered into the dialer/connecter program in windows at setup and that's it. 

I just enable 'wired connection' and give it this password and that's it?

---

### Post by zvacet on 2007-03-17
system>administration>network settings>highlight your modem>properties>select type of conection(dhcp,static)>chek upper left box>close>DNS>replace address you see with your own>close
```
sudo pppoeconf
```

---

