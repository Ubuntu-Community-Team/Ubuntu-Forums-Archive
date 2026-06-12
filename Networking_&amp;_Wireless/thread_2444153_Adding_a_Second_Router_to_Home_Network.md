---
title: "Adding a Second Router to Home Network"
date: 2020-05-25
forum: Networking &amp; Wireless
---

### Post by Shadius on 2020-05-25
Hi all,

I want to use my Cisco Linksys E1200 router to extend my network, both wired and wireless. It will have one PC connected to it through a wired Ethernet connection and all others will be wireless

I'm a bit confused as to how to set this up. 

I know I must disable DHCP on the Cisco Linksys E1200 router, but the addressing is what confuses me. 

My Verizon router's gateway IP address is 192.168.1.1, so does that mean I need to make my Cisco Linksys E1200 router's IP address under the Network section of the web interface to the same, or set it to something like 192.168.1.2? 

Please help!

---

### Post by TheFu on 2020-05-26
Do you want to filter traffic between the devices?  Probably not possible with the stated goal.

Do you want different devices to be on different subnets? Reads as no.

Do you want all the devices to be on the same subnet? 

Routing works by having different subnets on each side of the router.  You can use a router as a switch in many situations by not using the WAN port at all ... just disable all services on the Linksys, then plug in the different devices to the LAN ports, then connect 1 of the LAN ports to the Verizon router.  This will end up with a flat network.  With all the services on the linksys disabled, the Verizon will need to provide those.  If DHCP is disabled on the linksys, then addresses need to be either manually configured or DHCP provided by the Verizon.

You'll want to understand networking better to do much else.  As long as you are changing things, it really is best to never use 192.168.1.1/24 as a network anywhere.  Same for 192.168.0.1/24, 10.0.x.x/24 and 172.16.x.x/24.  Avoid those so you can have flexibility in the future for remote connections from a cafe or hotel.  The selected subnets still need to be in the RFC-approved private network spaces, but there are thousands of those.192.168.51.1/24 wouldn't be a bad choice, but really the "51" can be anything from 3 -to- 254 to achieve the goal.  The goal is never (as close to never as possible) be on a remote network with the same subnet.

To learn how networking works, search for episodes 25 of the *Security Now* podcast. It is the big picture ideas you need to understand. Details can be looked up as needed.

Have you considered using just a wifi AP instead?  Ubiquiti makes some for $50-$300 with PoE that can be placed almost anywhere. Because the power is over the ethernet cable too, we aren't restricted to locations with an electrical outlet. Consumer routers tend to lose vendor patch support in 3-4 years, so they really shouldn't be on any network. But Pro-sumer devices like MikroTek and Ubiquiti sell are maintained much longer.  Plus, wifi-standards are constantly changing so to get better, more secure, faster connections, we need to change wifi more often.  A bunch of new wifi gear is about to be released to support the newer standards, Wifi-6 (802.11ax) for example. [https://www.howtogeek.com/368332/wi-fi-6-what%E2%80%99s-different-and-why-it-matters/](https://www.howtogeek.com/368332/wi-fi-6-what%E2%80%99s-different-and-why-it-matters/)

If you need to get networking to different parts of the house between two APs/routers, I can suggest powerline networking, just expect about 10% of the bandwidth that the box claims.  So, my 600 Mbps powerline going between the home-office and downstairs to the opposite side of the house really gets only about 60 Mbps, but at least it is stable and encrypted.  On the same floor, between a room and hallway outside (shared wall), the bandwidth was 220 Mbps ... so for my house, the box's claims are pretty aggressive.  They make 1200 Mbps powerline pretty cheap these days.  It is stable bandwidth, not like wifi, which fluctuates massively.  We seldom need wifi where our routers are located. Think that's a universal problem.

I'm a little more security conscious than most, so I keep wifi off my main network.  Wifi can't really be trusted.

---

### Post by SeijiSensei on 2020-05-26
You can daisy-chain the routers by connecting the WAN port of the second router to one of the LAN ports on the first router, then giving it an address in the first router's network, 192.168.1.0/24 in your case.  So yes you could set the address of the second router to 192.168.1.2.  I've done that when I didn't want to muck with the router provided by my ISP.

However you should read the manuals for your hardware to see if you can use "bridging" to extend the range of your first router.  Sadly[this article](https://community.linksys.com/t5/Wireless-Routers/Configuring-e1200-as-wireless-bridge/td-p/532530) says the E1200 cannot do wireless bridging. Perhaps if you reverse the devices?  You'll need to read the manuals.

---

### Post by kurt18947 on 2020-05-27
I'm doing this with 2 netgear routers - close but not the same model. Both are running DD-WRT. The second router is also my wifi access point. I have Verizon FiOS with ethernet from the ONT. My configuration is ONT -> Router 1 WAN port. Ethernet cable from Router 1 LAN port to Router 2 LAN port. DHCP disabled on Router 2. Both routers have non-192.168.1.1 I.P. addresses but are on the same subnet. I also have a MoCA adapter plugged into one of Router 1's LAN ports so can have wired ethernet wherever there's a coax jack. It seems to work pretty well. I did try running the ethernet from Router 1 LAN port to Router 2 WAN port. I was able to get network access but couldn't figure out how to print to a printer with a static I.P. on Router 1's network.

---

### Post by Shadius on 2020-05-28
> **kurt18947 said:**
> I'm doing this with 2 netgear routers - close but not the same model. Both are running DD-WRT. The second router is also my wifi access point. I have Verizon FiOS with ethernet from the ONT. My configuration is ONT -> Router 1 WAN port. Ethernet cable from Router 1 LAN port to Router 2 LAN port. DHCP disabled on Router 2. Both routers have non-192.168.1.1 I.P. addresses but are on the same subnet. I also have a MoCA adapter plugged into one of Router 1's LAN ports so can have wired ethernet wherever there's a coax jack. It seems to work pretty well. I did try running the ethernet from Router 1 LAN port to Router 2 WAN port. I was able to get network access but couldn't figure out how to print to a printer with a static I.P. on Router 1's network.

This is how mine is currently set up. 

The Verizon Fios router has a MoCa connection with the coaxial cable. The second router (Cisco Linksys E1200) is connected to the first router (Verizon Fios) through the LAN ports on each side and the PC is connected to one of the other LAN ports on the second router.

---

### Post by slickymaster on 2020-05-28
*Thread moved to **Networking & Wireless**.*

---

### Post by Shadius on 2020-05-28
> **TheFu said:**
> Do you want to filter traffic between the devices?  Probably not possible with the stated goal.

Do you want different devices to be on different subnets? Reads as no.

Do you want all the devices to be on the same subnet? 

Routing works by having different subnets on each side of the router.  You can use a router as a switch in many situations by not using the WAN port at all ... just disable all services on the Linksys, then plug in the different devices to the LAN ports, then connect 1 of the LAN ports to the Verizon router.  This will end up with a flat network.  With all the services on the linksys disabled, the Verizon will need to provide those.  If DHCP is disabled on the linksys, then addresses need to be either manually configured or DHCP provided by the Verizon.

You'll want to understand networking better to do much else.  As long as you are changing things, it really is best to never use 192.168.1.1/24 as a network anywhere.  Same for 192.168.0.1/24, 10.0.x.x/24 and 172.16.x.x/24.  Avoid those so you can have flexibility in the future for remote connections from a cafe or hotel.  The selected subnets still need to be in the RFC-approved private network spaces, but there are thousands of those.192.168.51.1/24 wouldn't be a bad choice, but really the "51" can be anything from 3 -to- 254 to achieve the goal.  The goal is never (as close to never as possible) be on a remote network with the same subnet.

To learn how networking works, search for episodes 25 of the *Security Now* podcast. It is the big picture ideas you need to understand. Details can be looked up as needed.

Have you considered using just a wifi AP instead?  Ubiquiti makes some for $50-$300 with PoE that can be placed almost anywhere. Because the power is over the ethernet cable too, we aren't restricted to locations with an electrical outlet. Consumer routers tend to lose vendor patch support in 3-4 years, so they really shouldn't be on any network. But Pro-sumer devices like MikroTek and Ubiquiti sell are maintained much longer.  Plus, wifi-standards are constantly changing so to get better, more secure, faster connections, we need to change wifi more often.  A bunch of new wifi gear is about to be released to support the newer standards, Wifi-6 (802.11ax) for example. [https://www.howtogeek.com/368332/wi-fi-6-what%E2%80%99s-different-and-why-it-matters/](https://www.howtogeek.com/368332/wi-fi-6-what%E2%80%99s-different-and-why-it-matters/)

If you need to get networking to different parts of the house between two APs/routers, I can suggest powerline networking, just expect about 10% of the bandwidth that the box claims.  So, my 600 Mbps powerline going between the home-office and downstairs to the opposite side of the house really gets only about 60 Mbps, but at least it is stable and encrypted.  On the same floor, between a room and hallway outside (shared wall), the bandwidth was 220 Mbps ... so for my house, the box's claims are pretty aggressive.  They make 1200 Mbps powerline pretty cheap these days.  It is stable bandwidth, not like wifi, which fluctuates massively.  We seldom need wifi where our routers are located. Think that's a universal problem.

I'm a little more security conscious than most, so I keep wifi off my main network.  Wifi can't really be trusted.


Thank you for this reply. This has so much information! I'm afraid I don't know much about networking to provide answers to your questions, but I'll definitely check out the podcast in order to try to gain more knowledge.

---

### Post by kurt18947 on 2020-06-13
> **Shadius said:**
> This is how mine is currently set up. 

The Verizon Fios router has a MoCa connection with the coaxial cable. The second router (Cisco Linksys E1200) is connected to the first router (Verizon Fios) through the LAN ports on each side and the PC is connected to one of the other LAN ports on the second router.

Perhaps this is borderline necro but Verizon will switch the ONT from MoCA to ethernet with a phone call. I own the red & black Vzn router but it's limited to MoCA 1.1. I have two Ebay Netgear routers running DD-WRT so firmware is updated. I returned all the Verizon TV boxes and removed the Verizon router. I bought 2 Motorola MoCA 2.0 boxes, they provide MoCA networking throughout the house. One $20 8 port switch & some Tivo gear and I was in business. I figured about 20 months would pay for the new devices from savings on Verizon rentals. I do still have the Verizon router in case I need Verizon tech support beyond the ONT. So far I haven't needed anything support wise.

---

