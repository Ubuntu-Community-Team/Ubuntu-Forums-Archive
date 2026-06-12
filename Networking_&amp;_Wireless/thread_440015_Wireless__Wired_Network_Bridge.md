---
title: "Wireless / Wired Network Bridge"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by k3rst on 2007-05-11
Hello,

I've been trying to get my server box to work as a network bridge using ubuntu 6.10 server lately, and I'm kinda stuck at the bridging part. At the moment i have:

eth0 interface -> 10.2.0.10
wlan0 interface -> 10.2.0.11

my pc connects through wire to the eth0 port, and the internet comes from the wireless side of wlan0.
As it is right now, the server box can access the internet through wlan0 ( ping -I wlan0 [www.google.com](www.google.com) works ) . All i want is to bridge the two interfaces so my computer that is on eth0's side gets internet access. After some research I did online, it seems that the typical bridge-utils wont do because of a mac address confusion with the wireless card ( acx100 chipset). I also have parprouted installed but I'm not sure it does anything. 

Is there a way to either bridge or route the two interfaces ?

Thanks in advance

---

### Post by k3rst on 2007-05-12
Ok after some research online i found [_this_]("http://qtables.radom.org/files/quicktables-2.3.tar.gz") iptables script that helps you make your iptables rules through a number of questions and it worked fine!

---

### Post by rossperk on 2008-02-21
> **k3rst said:**
> Ok after some research online i found [_this_]("http://qtables.radom.org/files/quicktables-2.3.tar.gz") iptables script that helps you make your iptables rules through a number of questions and it worked fine!

I tried that script, but I keep getting stuck in this loop:

> i have determined that the interface that connects you to your ISP (untrusted network) is ath0.  is this the interface you want to use in your firewall script (yes/no) : **yes**

ath0 doesn't seem like a valid interface name

which interface connects you to your ISP (untrusted network): **ath0**

ath0 doesn't seem like a valid interface name

which interface connects you to your ISP (untrusted network):
(The bold being what I entered.)

---

