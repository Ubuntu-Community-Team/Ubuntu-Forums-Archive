---
title: "HP pavillion dv6206us"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by beakerman30 on 2007-03-08
Okay I have followed the instructions for getting a wireless card up and running and I seem to have hit a brick wall.... I go into the connection-manager and see the wireless networks and when I say connect it trys to connect and then never goes any further. The network I am trying to connect to is an unsecured and unencrypted wireless. I have an HP DV6206us and I have tried to no avail to find what the model of broadcom adapter i have. when I do an lspci I see that it says for the wireless that it is an unknown device ??

---

### Post by beakerman30 on 2007-03-08
Okay I take that back I was incorrect on the not connecting. I looked furhter into the connection and it is indeed connected with an IP however geting anywhere besides my machine is a lost cause. I tried pinging what i know is a server and it didn't even reach the server. I remoted into the server from another machine and tryed pinging back at my laptop and no luck there either. I can ping myself but that doesn't do me much good I am running Ubuntu-Edgy 6.10... anybody got some ideas

---

### Post by beakerman30 on 2007-03-08
Okay I did some more digging and I have noticed that I have an IP I have DNS which is correct. What seems to be causing the problem is that when I run an ifconfig the RX is showing lots of dropped packets ?? any ideas why my wireless would just drop packets.

Matthew

---

### Post by beakerman30 on 2007-03-12
Okay I installed wifi-radar and seem to be doing better now. I have noticed that the Unsecured networks seem to be the one that give me trouble connecting. IE I went to a hospital wifi and it sent out DHCP discovers and got nothing back. If I go home and try to connect i ge no problemo

---

### Post by beakerman30 on 2007-03-14
Okay I am getting desperate here. I have no problems connecting to secured encrypted networks but when I try to connect to an unsecured network I no go. I seem to not associate even if i go to the command prompt and type 

sudo iwconfig eth1 essid "insert network name here"

I thought mayhaps it was the driver so I followed some instructions in another post about how to uninstall bcm43xx driver blacklist it and install the broadcomm driver with ndiswrapper... Same results with this. I see the wireless network I just don't seem to be able to associate whicj of course means I don't get an IP 

Any info I can help supply to help solve this I will provide :)

---

