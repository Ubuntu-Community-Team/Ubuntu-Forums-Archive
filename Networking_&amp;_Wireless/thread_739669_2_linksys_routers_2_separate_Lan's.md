---
title: "2 linksys routers 2 separate Lan's"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by fain on 2008-03-29
Ok heres my situation. I have two separate Lan's The first lan contains 1 computer and the second contains 2 computers and a wireless. I have router A connected to the internet and router B is connected to Router A via its wan port. I run a server in router B's network. Is there a way i can get Router A's network to see the server in router B.

The internet can see this server fine. I have set up a static route on router A to router B's network. I can ping router B's network but cant get to the server behind router B.

Heres my topology
Internet
routerA's network = 192.168.0.1
routerA rout to routerB = 192.168.0.2
routerB's network = 192.168.1.1
server address = 192.168.1.2

as i said b4 the internet can get to the server but no computer can see it from the A network. 
I know i could use the router as a switch but for certain reasons i can not do this.

---

### Post by drdrewdown on 2008-03-30
NAT is your problem. avoid using the WAN port on the 2nd + beyond routers.  also be sure to disable DHCP in any router beyond the original.. i would recomend using LAN ip's at opposite ends of the spectrum.

router1 hooked up from port1 to router2's port 1
router 1 LAN ip= 192.168.1.1
router 2 LAN ip= 192.168.1.254
do not use WAN port on 2nd router
disable dhcp in 2nd router

this will make this 2nd router a switch, as all routers are switches with wan ports to create routing.  so just bypass the wan port & disable dhcp on the 2nd box & you're good.

---

### Post by fain on 2008-03-30
Hey, thanks for the response. I used to run my network this way but I need it this way for this reason. Router A has a voice system in it. It is in the room where the phone is so it cant be moved. (it is not my phone) Now RouterB Is running Linux(dd-wrt) I have a script set up to monitor the firewall log to forward a WOL packet to my server when the packet is accepted. Now, I believe this script will not work if the firewall is bypassed. As it would be when working as a switch. Thanks though.

I figured that setting up a static rout would work(the way it did in cisco class.)

The ultimate goal is this. I need my server to goto sleep, when some one accesses it, I need something to send a WOL packet automatically since not many people even know what WOL means. I'm just trying to save power and money. This way works fine but i just cant get the people in the next room to see my server :mad: which i don't understand cause the internet can see it fine.

I have DMZ enabled on the servers ip on both routers. A static route on router A. So when it receives a packet for 192.168.1.0 network it will forward it to 192.168.0.2 (routerB's address)
This works as i can ping 192.168.1.1 address from Network A but thats as far as i can get. Why wont routerB route my packet to the server like it does from the internet?

---

