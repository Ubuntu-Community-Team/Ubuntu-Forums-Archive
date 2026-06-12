---
title: "LAN - static IP question"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by wolfvorkian1 on 2007-08-29
I have 4 computers on this wired network. 1 of them is not physically accessible or more correctly is difficult to get to. 

For torrent downloads I would like to establish a static IP on these computers. For 3 of them, this a rather simple task to accomplish but a pain for the 4th because of access to it is difficult. 

So my question is, what happens if I give 3 of the computers a static IP and don't on one?

---

### Post by dmizer on 2007-08-29
a nat router configured with dhcp will be unable to keep track of static ip addresses on your network.  so you run the risk of your dhcp configured computer being assigned the same ip as one of your statically configured computers. = very bad.

if the "difficult to access" computer is on your network, can't you access it remotely with ssh or vnc?

you can also check your router to see if there is a setting to assign a specific dhcp ip address according to mac address.  this way, your 3 torrenting computers are always assigned the same ip, and your nat router will have a log of the lease and keep it from assigning the same ip to two computers.

---

### Post by wolfvorkian1 on 2007-08-29
The router seems to support the mac approach. I'll try it. Thanks for the help.

---

