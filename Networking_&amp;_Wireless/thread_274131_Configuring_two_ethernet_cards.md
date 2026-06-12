---
title: "Configuring two ethernet cards"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by blakegrover on 2006-10-09
Hi,

We have a department that uses ubuntu as their operating system and through the web browser that get the phone numbers and names to call people to give them bids.  We have a asterisk server (Linux pbx system) and I have configured the ekiga soft phones on all the boxes to dial out through our asterisk server.  Anyways here is the problem I am having:

I want to have two network cards in each machine and I have two separate networks.  One is the 192.168.0.1 which goes out through our company internet  connection.  The other network is the 192.168.20.1 network and they all go to a seperate switch that is hooked up to the asterisk server and a separate dsl line so that the voice calls do not get mixed in with our internal network/internet.  I have gotten two card sin one of the ubuntu machines and it is recieving an ip number from each dhcp sever ex 192.168.0.32 and 192.168.20.3 for each card.  The problem I am having is for some reason ubuntu wants to go out on the eth1 connection which is the 192.168.20.1 network and I want it to use the eth0.  In the networking configuration gui there is a spot to select which is the default card but it doesn't change anything all internet traffic goes out through the second card.  I also have a machine running edgy here and in the network settings screen in edgy it doesn't let you change the default card, so maybe it never worked in dapper after all.  Anyways I need to get it setup so ubuntu uses the eth0 card by default and then I need to setup ekiga to use the eth1 which it looks like I can do in the settings.

Thanks
Blake

---

### Post by mips on 2006-10-09
You have to change the default route to point to your gateway of choice and then you need to add an additional (static) route to the asterix box for the voice stuff.

what's the output of **route -n** ?

---

### Post by blakegrover on 2006-10-09
After I left the machine and came back it is now sending all default things out the eth0 and the ekiga software is going out on the eth1 network  here is what route -n showed

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         192.168.20.1    0.0.0.0         UG    0      0        0 eth1


I am going to be doing this on 8 other comnputers.  Is there a wayu I could use this route command to set up default routes to use eth0 for everything but the 192.168.20.0 network?

Thanks
Blake

---

### Post by spd106 on 2006-10-09
Open up a terminal and have a look at the routing table, either **route** or **ip route**. If you have more than one default route then you need to remove one.

---

### Post by blakegrover on 2006-10-09
From the output of the route -n it looks like the default gateway is the 192.168.20.1 which I do not want to have.  I also do not think I need the 169.254.0.0 or the 0.0.0.0 networks but maybe the 0.0.0.0.0 is a wildacard meaning everything else.  Is there a good tutorial on how to add and remove these routes?

---

### Post by mips on 2006-10-09
remove the current default gateway and add the correct one. Next add a normal route to the voice stuff

---

### Post by blakegrover on 2006-10-09
I am note sure how to add a route or delete them like I said above, do you know how or a website that can explain how to do it?

Thanks
Blake

---

### Post by blakegrover on 2006-10-09
I have found out how to delete the routes and everything is working fine.  

I ran route del -net 0.0.0.0 dev eth1 and it removed the entry

---

