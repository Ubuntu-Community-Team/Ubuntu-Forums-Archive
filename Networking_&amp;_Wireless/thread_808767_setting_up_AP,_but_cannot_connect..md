---
title: "setting up AP, but cannot connect."
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by davidcopper on 2008-05-26
Hi, all.

I insalled madwifi-ng on laptop A, and set it up as AP using :

sudo modprobe ath_pci autocreate=ap

sudo iwconfig ath0 essid myap.


From another laptop, B, I can see the name "myap" when scanning available networks. However, when I tried to connect to laptop A, laptop A could not assign an IP address to laptop B. 

I tried to use firestarter to sort out the problem. I set eth0 as external device, and (unknown) ath0 as internal device. When I finished, I got "ath0 is not ready".

Can anyone help me out? Im frustrated. I have searched a lot of documents online about setting up ap, but none of them tells you how to assign IP to clients. 

Many thanks for any help you may give.

Regards

Dave

---

### Post by superprash2003 on 2008-05-26
try setting up ip address on laptop B manually.. go to system->administration->network and choose ethernet card and go to properties and select "Static ip address "

---

### Post by davidcopper on 2008-05-26
HI,

Thank you for your advice. I think it will be better if I can get it assign IPs dynamically. Anyway I have worked it out. 

I forgot to set an ip for my internal device, namely ath0. so I just set it as, say, 192.168.0.1. Then I set in firestarter that assigning IPs for local network ( the one which gets Internet connection via ath0) in DHCP way. It works.


However, I'd like to know how I can build a bridge using command line utilities.

Many thanks for any advice you may give.

Dave

---

### Post by piotrwoj on 2008-06-11
Autostarting HOSTAP on madwifi
1) modprobe ath_pci autocreate=ap
2) nano /etc/modules
3) write to files: ath_pci autocreate=ap
4) /etc/network/interfaces:
iface ath0 inet static
address 10.0.0.1
netmask 255.255.255.0
#gateway 10.0.0.1 //- in NAT not necessary (DHCP3-Server)
wireless-key xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx
wireless-essid Your_Essid
#wireless-mode master - necessary only with prism2, 2.5

---

