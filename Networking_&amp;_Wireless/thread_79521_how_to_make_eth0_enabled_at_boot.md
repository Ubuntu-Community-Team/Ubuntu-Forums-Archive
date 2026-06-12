---
title: "how to make eth0 enabled at boot?"
date: 2005-10-20
forum: Networking &amp; Wireless
---

### Post by drtvasudevan on 2005-10-20
i had problems with connecing to internet and have been fiddling with settings.
now i can connect to internet afgter tweaking firefox.
but the eth0 is down by default and i have to go through terminal and enable it.
[it keepps giving error msg but does the job]
when i boot next time it is again down.
how do i make it stay up always?:confused: 
tv
newbie

---

### Post by chanders on 2005-10-22
Place 

auto eth0 

on the last line of your /etc/network/interfaces file. That should solve your problem! ;)

---

### Post by landotter on 2005-10-22
it should automatically be enabled at boot. In the network settings, double click on the properties for the connection and tick the box in the "enable this connection" dialog.

Or just do as the previous poster said. :P

---

