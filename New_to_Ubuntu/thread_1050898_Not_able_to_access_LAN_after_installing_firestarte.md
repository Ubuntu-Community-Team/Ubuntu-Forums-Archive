---
title: "Not able to access LAN after installing firestarter"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by id_virt on 2009-01-26
I wanted to share internet connection with others in the LAN almost all of them using windows. So i installed firestarter after i read about in forums.But after that i am not able to access the LAN.Others are not able to access net through my system.The network places is empty.I am using intrepid ibex.In firestarter eth0 is the network card to which internet connection is connected.It uses DHCP and lan card is eth1 which is manually configured to a static IP.

thanks in advance...

---

### Post by halovivek on 2009-01-26
Could you post these output?
sudo lshw -C network

route

ifconfig

iwconfig

---

### Post by zebanon on 2009-01-26
r u using ubuntu 8.10??
i can access LAN using ubuntu 8.10

---

