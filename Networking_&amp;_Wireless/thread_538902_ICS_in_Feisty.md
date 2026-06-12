---
title: "ICS in Feisty"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by blamecanada on 2007-08-30
I'm at a university and the wired network here is very laggy. As a result, I'm trying to connect to the wireless network (much less lag) and share that connection across to my Xbox 360 via Ethernet. I downloaded Firestarter to do this, but the network manager seems to only want me to have one connection at a time (either wired or wireless), so firestarter won't start because one of the devices is disconnected.

Basically I need to pull a signal off the wireless network and send it over a wired one. I'm running Ubuntu 7.04.

---

### Post by spd106 on 2007-08-31
I suggest that you turn off roaming mode and set a static configuration instead. This will allow you to have multiple interfaces active simultaneously. Use System -> Admin -> Network, rather than nm-applet.

If you need WPA, then you will have to edit the /etc/network/interfaces directly, see the Wireless Security sticky. Or you could wait for Ubuntu 7.10, which has better WPA support.

---

