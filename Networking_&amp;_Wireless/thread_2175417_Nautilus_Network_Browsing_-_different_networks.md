---
title: "Nautilus Network Browsing - different networks"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by stevenjrees on 2013-09-19
I have a wireless router and a wired LAN with computers on both networks. i.e. 192.168.1.x and 192.168.2.x
each computer can browse others computers within its own network, but can't see computers on the other network. 
each computer can ping other computers on the other network and visa-vie so no routing problems. all computers can route through a 3rd network to the interent

how can i setup ubuntu up so that the nautilus/gnome browser can see computers on both networks. 
this is currently a particular problem because i can print to the shared printer on the network that is not visible to the other side.

---

### Post by stevenjrees on 2013-09-19
so i figured out i had to modify the smb.conf file with two interfaces as network addresses. 
I can use smbclient to connect to machines across both networks
i can use nautilus "connect to server" to connect to a named server on the opposite network

however, the "Network" browser in nautilus still only shows the machines in the network attached to the network card

any help please

---

### Post by stevenjrees on 2013-09-19
another thing, 

smbtree shows me only the devices connected to the network directly connected to the machine where the command is being run.

however

nautlius smb://hostname opens up a correct window

---

