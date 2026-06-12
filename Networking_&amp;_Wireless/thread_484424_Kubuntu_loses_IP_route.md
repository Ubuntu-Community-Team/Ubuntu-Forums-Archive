---
title: "Kubuntu loses IP route"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by ed67 on 2007-06-25
I'm using Kubuntu 7.04 and I gather from other threads in forums that my issue is not unique.

It loses my IP route.  The internet works fine but I can't browse network files on other computers until I go to System Settings, Network Settings, switch to administrator, choose "Routes" tab and type in 192.168.1.1 and choose ath0 for my wireless card.

I apply my way out everything works, but then later it will not work anymore and I have to repeat the steps.  However the Internet always works just fine, even when the IP route reverts to 0.0.0.0

It sounds like this problem has been ongoing but I haven't yet found a solution that works.  Does anyone know what the problem is?  Worked fine in Ubuntu 7.04 and I'm new to Linux but I enjoy using it very much.  Any help would be appreciated.

---

### Post by Vola on 2007-06-26
There's is a gateway into your network interface config??

Please check the /etc/network/interfaces

and look if you have an entry like:

gateway 192.168.1.1

---

### Post by ed67 on 2007-06-26
Here is the contents of that file.  After I change the network settings, the contents of this file do NOT change.  I don't know if they're supposed to, but the network works until it loses the settings.


auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

---

### Post by Austin_KW on 2007-06-26
Sound like a dhcp client is running again and getting a response without default route.


What is the output of the following terminal commands
ifconfig
route


dif you try the suggestion of adding gateway 192.168.1.1 for ath0 in /etc/network/interfaces

---

### Post by ed67 on 2007-07-05
> **Austin_KW said:**
> 


dif you try the suggestion of adding gateway 192.168.1.1 for ath0 in /etc/network/interfaces


No, exactly what do I type?  And where in the file would I type it?  Thanks.

---

