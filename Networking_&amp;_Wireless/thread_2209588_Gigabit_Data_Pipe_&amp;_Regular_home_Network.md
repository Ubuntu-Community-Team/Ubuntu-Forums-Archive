---
title: "Gigabit Data Pipe &amp; Regular home Network"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by jake22 on 2014-03-06
Hello, 
I have two computers FortDoe  and BluFort. 
Blufort is a ubuntu system with ssh,vnc,smb, and it also runs a bitminer. It has two network cards a gigabit and a megabit card. 
FortDoe is my main tower running windows 7, It's my main system and it also has the same network card setup

My home network conesists of Three routers 
A = Main internet gate way \ wifi point (Conected to it is fortdoe and Blurouter) router 192.168.1.1 and DHCP is running on A only
B = BluRouter conects to main by 100ft cable, It provides wifi and lan ports to my back room, and is also connected to router C via 100ft, 
C= conects to Blufort and more systems 
My home network is fully 10/100 compatible....kind of a downer... dd-wrt is cool 

So I ran a Ethernet cable between my tower and my ubuntu box, I get decent gigabit enternet speeds between the two computers, (The cable is over 100 feet and I get about 40-70 megabites \s)

The thing is though on the windows 7 tower I have to use the IP of the ubuntu box and vise versa. I addressed my two systems as 
fortDoe 10.0.0.1 and blufort 10.0.0.2 on the gig cards
 
I would also like to just be able to browse the shares on blufort with the network neighborhood in windows with the Computer name, connecting though the network browser or by useing Blufort cuases my tower to use the home network and not the direct conection. Equaling in to a very slow tranfer with higher latency because FortDoe is conected to router A with a long cable, and BluFort is connected to the internet via router A > B > C  If I use my home network the data has to go over 300ft of cable  


I've goten quite far with no help, from not knowing much about linux and being a windows user, 

anyways, Thanks for all the help and stuff

---

### Post by TheFu on 2014-03-07
Add the IP addresses for both machines to the /etc/hosts and the equiv on Windows. Then they will be able to find each other.

Also, it is unclear to me what port speeds your networking equipment supports on-both-the-LAN-and-the-WAN interfaces.  That second router probably isn't needed - a $15 GigE switch would be fine.

---

### Post by jake22 on 2014-03-09
> **TheFu said:**
> Add the IP addresses for both machines to the /etc/hosts and the equiv on Windows. Then they will be able to find each other.

Also, it is unclear to me what port speeds your networking equipment supports on-both-the-LAN-and-the-WAN interfaces.  That second router probably isn't needed - a $15 GigE switch would be fine.


They can find eachother. Thats not the problem The problem is they are seeing eachoteer on the 100mb network. 

I have a direct cable between the two systems on there gig network cards, I can go to the systems via IP, But if I use the host name it defaults to the home network, not the direct conection. 

Seriously why should I spend 15 bucks because im connecting two computers via a direct network cable? It works, Just not excatly how I want.

---

### Post by TheFu on 2014-03-09
Please run
* ifconfig 
* route
on both systems and post the results.  In the old days, a normal ethernet cable didn't work when directly connected between systems. Do your NICs automatically swap the pins so a cross-over cable is NOT needed?

We'll look at the metric for each connection, validate they are on different subnets and that the routing makes sense.

Sometimes routers don't work the way you want if the knowledge of networking isn't strong, and if a $15 dumb, gige switch solves the issues ... how much is your time worth? That is the trade-off.

---

### Post by jake22 on 2014-03-09
look up gigabit networking, You dont need a cross cable for 1000mb enthernet. 


Home Network ( a regular routed network) 
IP 192.168.1.X
Netmask 255.255.255.0
Route 192.168.1.1

Direct Conection 
Ip 10.0.0.1
netmask 255.0.0.0

Ipconfig on BluFort Ubuntu

Home Net 
192.168.1.x
255.255.255.0
192.168.1.1 

Direct Conection
10.0.0.2
255.0.0.0

what exactly do you want with the route comand? 
And seriously I rather make it work then pay 15 bucks for another power brick 

The direct connection works if I manual connect with the IP, just though the system names or via network browsers it defaults to home net. how do i fix that?

I will make a network diagram to help make my setup uderstandable

---

### Post by TheFu on 2014-03-09
Automatic cross-over is an optional part of the 1000base-T 
[https://en.wikipedia.org/wiki/Auto-MDIX#Auto-MDIX](https://en.wikipedia.org/wiki/Auto-MDIX#Auto-MDIX)  - optional. That means it may NOT be part of any specific NIC.
> This may or may not be implemented on a given device, so occasionally a crossover cable may still be necessary when connecting auto-MDIX to MDIX

If you don't want to post the requested output, fine.  I just wanted to help.

---

### Post by jake22 on 2014-03-09
Look, the two computers are talking and are networking fine on gigabit.  So get over how its just working Fortdoe has a p5k-vm main board, trust me its working 

I want to know what you want from the routes, because its a dos prompt. cant copy and paste it,

---

