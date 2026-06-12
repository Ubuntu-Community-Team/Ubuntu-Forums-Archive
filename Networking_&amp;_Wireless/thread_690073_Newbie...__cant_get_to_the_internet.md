---
title: "Newbie...  cant get to the internet"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by heron98105 on 2008-02-07
Cant get to the internet. 

I can see eth0 and have given it a static address... no good.
Tried to have it use DHCP like all of the MS boxes are using.. no good.

P4 Asus MB with onboard Marvell gigabit adapter.

I did the lsmod in the terminal and neither tulip or lmfe are listed.

Any help would most appreciated.

Thanks

---

### Post by hahahan on 2008-02-07
Can you try it from terminal:

sudo ifconfig eth0 up
sudo dhclient eth0

What is the output of dhclient?

Regards.

---

### Post by heron98105 on 2008-02-07
It is not receiving any DHCP offers. My internet connection is Comcast Cable Modem. The windows machine renews everytime. I have verified known good cable.

---

### Post by hahahan on 2008-02-08
Can you post the output of :

lshw -C network

Your card might not be supported by Ubuntu.

---

