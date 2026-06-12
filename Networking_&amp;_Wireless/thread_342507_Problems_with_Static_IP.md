---
title: "Problems with Static IP"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by evanmanny on 2007-01-20
I just added a new computer running fluxbuntu to my home network and I'm having some trouble getting it to work with a static ip address. I added a

[INDENT]iface eth0 inet static
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.1[/INDENT]

entry to /etc/network/interfaces just like I did with a wireless laptop on the network. I then added this ip address as static on my router's configuration page. Then under my router's advanced configuration I added a new entry with the same information as a gateway. I don't know exactly why I do this, but I figured out that it worked when I was getting the laptop to work. Anyway, this computer won't connect to the outside world. It connects to the router configuration page fine but nothing beyond that. I'm guessing this means it has something to do with gateways although I don't really know. Any input?

---

### Post by teaker1s on 2007-01-20
put your isp DNS in ubuntu as it sounds like ubuntu is not resolving it from the router:)

---

