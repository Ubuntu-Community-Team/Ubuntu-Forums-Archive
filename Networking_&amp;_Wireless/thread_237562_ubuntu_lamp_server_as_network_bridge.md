---
title: "ubuntu lamp server as network bridge"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by dmizer on 2006-08-16
actually i'm not really sure of the technical terms for the configuration i'm attempting to create so sorry for the terrible title if i'm on the wrong track.  networking is not a strength of mine.

i have a network where, for file sharing security concerns, i'd like to isolate the clients from the direct connection to the internet.  i also need to have a lamp server in place.  so i am trying to configure the network as follows:

dsl modem -> hardware router/firewall -> lamp server -> router -> networked clients.

the lamp server has two network adapters.  it is set up with static ip from the hardware router on eth0. i would like the second network adapter (eth1) to function like a modem to the second router such that the lamp server has static ip on both eth0 and eth1.

several reasons for desiring this particular configuration.

1) most importantly, this way i can have static ip for connections to the server both lan and wan side while still allowing the clients to have dhcp configurations.

2) i will need to have ssh and several other external ports open on the wan side of the lamp server and i don't want the insecurity of having the server route wan requests to itself.

3) it is essential that the networked clients have a dhcp connection.  but i realize the server's best connection is static ip.

in any case.  i don't have a problem configuring the wan side.  but the lan side is beyond me.  how do i set up eth1 such that it will function as a though it was a direct connection to the internet.  ie, plug the lan cable from the server into the wan port on the router.  and then have the router assign dhcp to the network.

i realize i could probably configure as | modem -> server -> hub | and simplify things, but there are security concerns that i have to address.  namely a hardware firewall in place between the modem and the server.  as well as serviceability concerns, namely a dhcp lan and static server.

these are not my restrictions to give or take, so i have to answer them because it is not my network.  anyone else with suggestions on how these restrictions can be met are welcome to share, but i'd really just like to know how to set up eth1 for connection to the lan router.

---

### Post by dmizer on 2006-08-17
okay ... let me try this again.

i want to connect an ethernet cable from the eth1 port on the server to the wan port on the linksys and have the linksys retrieve an ip (on a different subnet than the wan) from the server.

to complicate issues, this needs to be configured via cli.

is what i'm asking really that difficult?

---

### Post by Bakerconspiracy on 2006-08-17
I don't think you can do static and DHCP with two different routers on the same network but I might be wrong.
 What i would try is (if you have the parts)try to configure the first router with the statics then configure 
the second with DHCP in a range that will not conflict with the already assigned static ips on the network. 
This architecture seems impractical though. Whats the point of having static ips if you are just going to assign 
them in a different part of the network? Why dont you just do Modem>Gateway Router/Hardware FireWall(DHCP)> Lan w/ LAMP server?

---

### Post by Soarer on 2006-08-17
Shouldn't be a problem. I don't have the 2nd router between server & users, but I have 2 LAN cards, one with DHCP to the ADSL router & the net, one to the clients which has a static IP & gives out IP addresses to clients using DHCP.
The only complication I can see is to set the 2nd (internal) router to pass though the DHCP requests and the returning addresses, for which you will have to turn off its DHCP server. Alternatively, you could let the internal router serve the DHCP in the same sub net (but not the same IP obviously) as the static IP LAN connection on the server. Come to think of it, as its a router you could give out a completely different range & route to the static IP.
I don't use Linksys so can't give you the cli commands for that - I always try & do it by router gui as the clis are usually badly documented.
OTOH - maybe I misunderstood your question?

---

### Post by dmizer on 2006-08-17
well, for website hosting purposes, we'll need static ip for port forwarding, so there's not really a way around using anything but static at least on the wan side of things.

i might be able to talk the boss into a configuration where the second router connects directly to the first and distributes dhcp to the rest of the network clients.

the main idea here is that the sever will need to be attached via static, and the network clients need to be dhcp.  so i will see if there is potential in the router (static) to router (dhcp) configuration.

---

