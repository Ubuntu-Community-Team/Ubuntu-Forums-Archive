---
title: "Apache, php fsockopen() and two NIC's"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Mishkin_85 on 2007-05-07
Hello,

I'm having a small problem with a server I'm trying to set up. I've got a tini-card acting as a webserver on my local network, connected with a crossover cable to my real webserver, running Ubuntu and Apache2. This real webserver is connected to the schools network and gets it's ip from the dhcp-server.

The /etc/network/interfaces file looks something like:

auto eth0
iface eth0 inet dhcp
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet static
address: 192.168.0.1
netmask: 255.255.255.0

The tini-card is connected to eth1.
Apache is serving the site on eth0.
I'm trying to get php to access the tini-card on eth1, using fsockopen with the tini-cards ip, 192.168.0.15.

It just seems like the php-script cannot access the local network, what am I doing wrong? Do I need to add some sort of bridge or route to make this work?

I can telnet 192.168.0.15 just fine, but the website won't work.

Any help would be appreciated, I'm not that good with these networking things... :)

---

### Post by Mishkin_85 on 2007-05-09
Nevermind, solved the problem after looking through the code about 15 times, missing a space between "Connection:" and "Close".

Silly :)

---

