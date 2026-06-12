---
title: "virtualbox thin client ltsp"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by atisz on 2008-10-22
hi

i would like to simulate a thin client network via ltsp 

it says:

"Configure your spare interface for the thin clients to have the IP 192.168.0.1 (and make sure it is up and running), then follow the instructions below."

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

so that i dont have 2 network adapters, i want to try it on virtualbox
simulating a server with 2 network adapters and a client connected to the server

do you guys have any suggestions how to implement this?

what configurations do i have to set in the network tab? I assume there 
should be adapter2 enabled too. The second interface should have the IP as above, but in virtualbox i can not set the IP. 

Can you guys help me with it? 

thanks

---

### Post by smartboyathome on 2008-10-25
Well, do you have a Wireless Card and an Ethernet card? I think that you could use the wireless card and ethernet card as your two networks, the wireless card using NAT (by far easier, and you don't need an IP for accessing the web), and the ethernet card using bridge-utils as described [here]("https://help.ubuntu.com/community/VirtualBox#Networking"). That is what I am assuming the two network cards are for.

I'm looking to do a similar thing with an old laptop I have. [Here is a post]("http://ubuntuforums.org/showthread.php?t=711235") which may help you, as it is a similar thing to what you have.

---

