---
title: "dealing with duplicate SSIDs"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Muchacho_Gasolino on 2007-02-08
Hey Ubuntu Folks,
I'm having a problem connecting to the wireless at my school. The university's access points don't broadcast their SSID. This wouldn't be a problem, but there is a bug in Windows where anytime a computer loses its wireless connection, Windows sets up a peer-to-peer wireless network with the same SSID as the last wireless network the computer was connected to and broadcasts it. So, anytime somebody loses their school wireless connection, a network pops up with the same SSID as the network. There are usually three or four of them whenever I search for networks. 
So, if i tell networkmanager to connect to the network with SSID abcdef, instead of connecting to the one i want it to, the access point that is hiding its SSID, networkmanager attemps to connecting to the abcdef peer-to-peer network that it can already see.
Is there any way to tell networkmanager to only connect to access points, or any other way to specify which network to connect to if it can't automatically see the SSID?

---

### Post by spd106 on 2007-02-09
This page is quite useful for questions regarding network manager [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

---

