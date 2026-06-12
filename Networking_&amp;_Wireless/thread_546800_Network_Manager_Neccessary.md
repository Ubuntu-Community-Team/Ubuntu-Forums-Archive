---
title: "Network Manager Neccessary?"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Worbly on 2007-09-09
Just wondering: If I specify the ESSID and WEP key in the /etc/network/interfaces file, do I need to have the Network Manager installed? 

I'm concerned that it might be interfering with my connection somehow. The connection succeeds whenever I restart the computer or boot up after shutting down, but for some reason if I boot up after hibernating the computer, it fails to assign me an IP address.

---

### Post by Spear on 2007-09-09
> **Worbly said:**
> Just wondering: If I specify the ESSID and WEP key in the /etc/network/interfaces file, do I need to have the Network Manager installed? 

I'm concerned that it might be interfering with my connection somehow. The connection succeeds whenever I restart the computer or boot up after shutting down, but for some reason if I boot up after hibernating the computer, it fails to assign me an IP address.

Hi !
you could fill in the interfaces file, but it's not the matter for now.

Back to a bash window :

Let's say your network interface is named "eth0" (check with ifconfig command)

If it's a renewal matter, try :
*sudo dhclient eth0*
(not sure it works with network manager, but ...)

If it doesn't change anything, try :
[I]ifconfig eth0 down
ifconfig eth0 up[/I]

Does any of these work ? try both, in order ...

---

### Post by Worbly on 2007-09-09
Maybe I wasn't very clear in my first post -- I have to specify the ESSID and Wireless key in the interfaces file in order for my connection to work at all. My question is, given that I have these things specified, will it do any damage to remove the network manager? Might that solve the trouble that I have which is that the connection doesn't work automatically when the system is booted after hibernation?

---

### Post by Spear on 2007-09-09
I'm not sure it'll change anything with the fact you loose your ip once you reconnectafter an hibernation ... i'll check if i can find anything new about that hibernation & dhcp

---

