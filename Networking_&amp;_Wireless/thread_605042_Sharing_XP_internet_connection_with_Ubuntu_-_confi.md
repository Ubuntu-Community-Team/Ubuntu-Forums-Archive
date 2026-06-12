---
title: "Sharing XP internet connection with Ubuntu - configuration problem"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2007-11-06
I have an XP machine which is connected to the internet. My Ubuntu 7.04 server ( no X-windows) is networked to the XP machine via a crossover patch cable. I can SSH to the Ubuntu fom XP using Putty.
What I wanted to do was to share my net connection with the Ubuntu machine, the subtle difference to usual ICS being that I want to Putty SSH into my Ubuntu box whilst it is sharing the connection and use [COLOR="Red"]wget[/COLOR] and [COLOR="Red"]apt-get[/COLOR] to download files and install / update software.
I'm  slightly confused with the configuration side of things.

[COLOR="Red"]XP - Machine[/COLOR] :
----------------
Network Connection Settings :

[COLOR="RoyalBlue"]NIC (1)[/COLOR] which is connected to the net :
Automatically obtains IP ADDRESS

[COLOR="RoyalBlue"]NIC(2)[/COLOR] which is connected to my Ubuntu box via xover cable :

IP Address : 192.168.0.1
Netmask 255.255.255.0
Default Gateway 192.168.0.1
[COLOR="Red"]
Ubuntu Box[/COLOR]

/etc/network/interfaces :

[COLOR="RoyalBlue"]#The primary network interface

auto etho
iface eth0 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1[/COLOR]

/etc/resolv.conf

[COLOR="RoyalBlue"]nameserver 192.168.0.1[/COLOR]

I am getting no connection  but am I on the right track ? Could anyone see errors in my configuration or enlighten me on anyhting I have omitted.
Thanks again.

All good wishes,
Uncle-C

---

