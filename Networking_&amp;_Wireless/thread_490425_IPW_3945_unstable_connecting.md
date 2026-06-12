---
title: "IPW 3945 unstable connecting"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by cat on 2007-07-02
Hi,

I am trying to use an Intel wireless card (IPW3945). It worked with the live cd and it also connected once via the network manager.

But usually it fails to receive an IP.

/etc/network/interfaces is empty except
auto lo
iface lo inet loopback

the module ipw3945 is loaded

the network (including acess point) is recognized. 
sudo ifup eth1 gives ....no dhcpoffers...

I don't know what the problem could be... Anyone?

---

### Post by TrueJk7 on 2007-07-02
Yes,

Run the command "sudo iwconfig" and see if it's got any access point associated with it. If not for now you can do it manually. 
# sudo iwconfig eth1 essid (your ID) mode managed
# sudo dhclient eth1

I actually use the same wireless card in a Dell. I had problems until I udpated from 6.10 to 7.04 the made sure I updated the driver.

---

### Post by cat on 2007-07-04
Thanks for the reply...It seems to work now :) I still don't know what the problem was.

---

