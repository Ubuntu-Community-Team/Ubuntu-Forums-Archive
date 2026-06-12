---
title: "EtherApe help"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by malfist on 2007-07-02
EtherApe isn't quite working for me for some reason. I installed it from aptitude (if that matters).
The problem:
When I launch the program from the menu, I get an error that no suitable device is found. To get it to use wlan0 I have to run it with sudo from the command line. But then it doesn't show the other computer on the network, granted, it is connected to the switch by Ethernet, but it should still show up.

Any ideas on how to fix this?

---

### Post by chili555 on 2007-07-03
According to this: [http://sourceforge.net/forum/forum.php?thread_id=1274966&forum_id=8023](http://sourceforge.net/forum/forum.php?thread_id=1274966&forum_id=8023) it *must* be run as root, or sudo for us in Ubuntuland.

---

### Post by tturrisi on 2007-07-03
> **malfist said:**
> EtherApe isn't quite working for me for some reason. I installed it from aptitude (if that matters).
The problem:
When I launch the program from the menu, I get an error that no suitable device is found. To get it to use wlan0 I have to run it with sudo from the command line. But then it doesn't show the other computer on the network, granted, it is connected to the switch by Ethernet, but it should still show up.

Any ideas on how to fix this?

AFAIK you cannot sniff or monitor net traffic of a computer on a switch, it must be on a hub.  A switch routes traffic ONLY to & from the specific mac address of the adapter, whereas a hub routes to all comnnected adapters.

---

### Post by malfist on 2007-07-04
[http://sourceforge.net/forum/message.php?msg_id=3505774](http://sourceforge.net/forum/message.php?msg_id=3505774) According to that, I should be able to set my switch (WRT54G (linksys)) to analisys/roving and I can't figure out how to do that. Does anyone know?

---

### Post by malfist on 2007-07-04
The router is WRT54G

---

### Post by malfist on 2007-07-04
I can see something, mostly between HOME (computer name) and MSHOME(computer workgroup).

---

### Post by malfist on 2007-07-04
Sorry for the quadruple post but the packets I'm getting don't seem to be TCP streams, just IGMP, NBNS, and BROWSER. I know there should be some TCP streams from internet traffic but I can't see them.

edit: can't count

---

### Post by tturrisi on 2007-07-04
According to this:
> [http://sourceforge.net/forum/message.php?msg_id=3505774](http://sourceforge.net/forum/message.php?msg_id=3505774)
Etherape can "see" only the traffic phisically passing on the netcard wire. Many small network use hubs to connect computers, so every packet is phisically transmitted to every netcard. 
A larger network use combinations of switches and routers, sometimes even firewalls to connect nodes, so your network card receives only its own traffic or broadcast. 
To monitor an entire network you can enable analisys/roving mode on your switch (essentially copies all traffic to a single port). If you have multiple switches, or routers, or the total bandwith exceeds the port maximum, you still will see only part of the traffic. 
If you only want to monitor internet traffic, you need to place etherape on the internet gateway.
you CANNOT monitor ALL TCP traffic on your LAN because you do not have a managed switch.  The switch in your router-ap is NOT a managed switch.  It's a generic low cost switch.  Some switches, such as stand alone connercial models, are managed switches with a web interface that can be used to config advanced switching.  The web interface to home routers don't really config the switch, the interface configs dhcp & network address translation, firewalling and that's about it.

To do what you want to do with etherape (or any other LAN monitor) you must:
1. connect modem to router-ap
2. connect a hub to the router
3. connect etherape pc to the hub
4. connect LAN pcs to the hub (that you wish to monitor)

You can't monitor LAN pcs connected to a switch UNLESS the switch has analisys/roving mode, your's doesn't.

---

### Post by malfist on 2007-07-04
I've got an old 4-port wired hub. If I connect the modem to the hub, to the switch. Then connected the other computer to the hub and this computer to the switch (because it's wireless), would I be able to see it?
Me to switch
Other computer & switch to hub
internet to hub to switch to all computers

---

### Post by tturrisi on 2007-07-04
NO, because for any comp to get an ip address from the router it needs to be connected to the switch after the modem.  Modem give 1 ip adxdress to router  Router dishes out up to 253 ip addresses.  You cannot do what you want to do unless you have a separate access point connected to the hub after the router.

modem > router/switch > hub > comps
..................................... | 
............................ access point > wifi clients

---

### Post by malfist on 2007-07-04
How would that work? Wouldn't the switch still be hiding the comp?

Sorry if I'm not understanding networking the best. My hub can do DHCP so it can assign IP's

---

### Post by tturrisi on 2007-07-05
> **malfist said:**
> Sorry if I'm not understanding networking the best. My hub can do DHCP so it can assign IP's

What you may not be grasping is a switch only routes traffic to a single mac address, a single destination.  While a hub routes all traffic to all connected mac addresses.  Your router uses NAT & DHCP, which assigns ip addresses to the connected computers, including wifi computers.  The router's ip address comes from the modem.  The router has 2 ip addresses, a WAN address from the isp and a LAN address 192.168.x.x).

If you place the hub between the modem & the router, then any computers connected to the hub won't get assigned LAN ip addresses by the router, thus they won't have Internet access. Also,  I have never seen a hub that has its own DHCP server. 

If the hub is placed between the router and the LAN computers, then ALL traffic that passes through the hub will be available to ALL computers that are connected to it, thus one could then sniff ALL the traffic going to & fro the computers connected to the hub.  The outbound traffic is sniffed BEFORE it arrives at the switch and the inbound traffic is sniffed BEFORE it arrives at the destination computer. 

> How would that work? Wouldn't the switch still be hiding the comp?
The switch is in front of the rest of the computers, the outbound traffic is sniffed BEFORE it arrives at the switch and the inbound traffic is sniffed BEFORE it arrives at the computers.  The switch in the router sends inbound traffic to a specific mac address (1 computer only) but the hub makes that traffic available to all computers connected to it.

Because your router has a built in AP, then any wifi computer is connected via the router's switch.  The router bridges the switch & the AP together.   Thus you cannot sniff traffic using a wireless computer.  The only solution is to disable the router's AP and then use a separate standalone AP that is connected to the hub.  The AP would get its LAN ip address from the router.

Years ago, isp's didn't filter ports.  Thus, one could sniff & map ALL traffic on the isp network.  That was a lot of fun!  One could then connect to default shares on Windows computers just by changing one's workgroup name.

---

### Post by nocturn on 2007-07-05
> **tturrisi said:**
> AFAIK you cannot sniff or monitor net traffic of a computer on a switch, it must be on a hub.  A switch routes traffic ONLY to & from the specific mac address of the adapter, whereas a hub routes to all comnnected adapters.

Unless you poison the ARP stack, takes a couple of minutes to complete

---

### Post by malfist on 2007-07-05
> **tturrisi said:**
>  Also,  I have never seen a hub that has its own DHCP server.
It's an old netstat one that I bought on clearance at walmart. It has four ports to lan four computers or if you push a button, it has one for the internet and 3 for the lan (which will get the internet). Port 2 never works, Port 1 and 4 always works, and port 3 does sometimes (and that was out of the box).

---

### Post by Entity` on 2008-04-16
> **tturrisi said:**
> If you place the hub between the modem & the router, then any computers connected to the hub won't get assigned LAN ip addresses by the router, thus they won't have Internet access. Also,  I have never seen a hub that has its own DHCP server. 

But in theory, you could use your computer as a dhcp server.  I doubt it would work very well.

---

