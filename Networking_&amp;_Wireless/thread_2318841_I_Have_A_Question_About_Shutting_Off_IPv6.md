---
title: "I Have A Question About Shutting Off IPv6"
date: 2016-03-29
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2016-03-29
My VPN for some reason only accepts IPv4 address's!  They told me with Ubuntu I can enable the OS to only accept IPv4.  I've temporarily shut IPv6 address's off on my router, but would like to turn it back on since there are other users on my network.  Also I want to make sure it's working properly when I'm on other networks.  I know I go into Edit Connections, but don't know where to go from there.  Also, isn't there a way to do it so it's automatic and I don't have to do it whenever I'm on other networks?  :confused:

---

### Post by Bucky Ball on 2016-03-29
Edit connections> Edit the connection you are wanting to close IPv6> Click the IPv6 tab> set to 'Ignore' (I think it is 'auto' by default).

---

### Post by shane_faulkinbury2 on 2016-03-30
Okay, that works for the network I'm on, but there's not a default for all networks?  When I click on Edit Connections it brings up all the networks in my area.  There is nothing about IPv6 and you have to select a network to see IPv6 options!

---

### Post by Bucky Ball on 2016-03-30
You're only connected to one network: your own. The other networks shown are available, but you're not connecting to them, so makes no difference about IPv6 or anything else. You probably can't connect to them if you tried as they are probably secure networks anyway.

Only worry about the network you are connected to, all other available networks have nothing to do with it. They have no bearing on your connection with your own network. Unless you're connected to it, irrelevant to you. ;)

(PS: Edit Connections should only give you a selection of the network you're connected to or networks you have connected to in the past. All available networks shouldn't be shown there. They should be shown when you click the network icon. If you've tried to connect with every available network, without success, then you may have entries in you Edit Connections for them. Delete them from there and leave only your network as the others are redundant.)

---

### Post by shane_faulkinbury2 on 2016-03-30
Okay, I get it.  I guess if I connect to another network I have to put in the password anyway so If I fix the IPv6 shut off at the time it will my system will remember it anyway!  :)

---

### Post by Bucky Ball on 2016-03-30
You got it. ;)

Yes. However you set up the connection, when you are connect to it again, Network Manager will remember your settings. We go see the in-laws two or three times a year and all I need to do it switch on and I'm on their network. Network Manager remembers everything from last time I was there, including the password. 

To do this, in Edit Connections> Edit> General tab, tick 'Automatically connect to this network when available' for your network. If you visit other networks in other locations, do the same for those connections. 

If you are going to use a static IP address, Edit Connections is also the place to set that up. Use the IPv4 tab, change to manual and set up the static IP. :D

---

