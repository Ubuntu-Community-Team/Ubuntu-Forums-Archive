---
title: "Networking Guru's input needed"
date: 2018-03-26
forum: Networking &amp; Wireless
---

### Post by bosscheesemo on 2018-03-26
Ok so I'm going to be moving in with some buddies here in a few months. We're all pretty heavy bandwidth users so a typical home network scheme of a single router with a switch or two connected for devices isn't going to cut it. I'm applying my basic networking knowledge (read: no formal IT training) to setting up a network scheme that will work for us. The routers being used are an Archer C7 for the main router, a Netgear r6200 for my secondary router, and the other two routers are unknown at this point.

Here is the planned topology:

The master router is connected to the modem and has IP address 192.168.1.1/24. Each of the master router's ports goes to one roomate's secondary router with one port being unused/for network maintenance. They will be numbered from 192.168.2.1/24, 192.168.3.1/24, and 192.168.4.1/24. Currently the network is comprised of the main router and my secondary router at 192.168.2.1/24. Physically, the main router is going to be in a central location and the secondary routers will be distributed to where each respective person is likely to use it most (i.e. bedrooms).

A.) The idea is that each network must be its own subnet that can access the internet but not be accessible from each other for the sake of privacy and to reduce broadcast interference. I can't subnet for anything: do I have the correct addresses assigned and the correct subnets assigned for this to work? My computer is connected to the secondary router and has connection to the internet but if there's a better way to handle this then I'm totally open to changing things.


Next some thoughts about WiFi in this setup. There are two different schools of thought here. One school of thought is that we want a public network that spans the house (2.5GHz band) plus our individual WiFi networks (5 GHz bands) available close to our routers. The other school of thought is to dispense with the public channel and simply give everyone their own 2.5GHz and 5 GHz band to do as they wish and then use personalized WiFi extenders where necessary to give everyone solid access throughout the house. 

B.) What are all the pros and cons to these schools of thought? I understand some of these pros and cons, but I need a rundown to present to the roomates so we can arrive at an agreed-upon decision.

C.) Is it possible to configure the secondary routers' 2.5GHz band to be extensions of the main router's 2.5GHz band whilst keeping the respective 5GHz bands segregated?

D.) Stupid question: Is configuring all four routers' 2.5GHz band to the same SSID and password equivalent to extending the networks?

E.) Stupider question: if a router is configured as a wireless AP, can a hardwired laptop connected to one of its ports still get network connection?


Thank you everybody!

---

### Post by chili555 on 2018-03-27
> A.) The idea is that each network must be its own subnet that can access the internet but not be accessible from each other for the sake of privacy and to reduce broadcast interference. I can't subnet for anything: do I have the correct addresses assigned and the correct subnets assigned for this to work? My computer is connected to the secondary router and has connection to the internet but if there's a better way to handle this then I'm totally open to changing things.

May I assume that the secondary router(s) is/are connected by ethernet? I hope so.

> Next some thoughts about WiFi in this setup. There are two different schools of thought here. One school of thought is that we want a public network that spans the house (2.5GHz band) plus our individual WiFi networks (5 GHz bands) available close to our routers. The other school of thought is to dispense with the public channel and simply give everyone their own 2.5GHz and 5 GHz band to do as they wish and then use personalized WiFi extenders where necessary to give everyone solid access throughout the house. 

If the goal is to provide privacy, then it is counter-productive to have any public wifi. Given a choice, I’d set up each router to have it’s own wifi, each with its own separate SSID.

> B.) What are all the pros and cons to these schools of thought? I understand some of these pros and cons, but I need a rundown to present to the roomates so we can arrive at an agreed-upon decision.

C.) Is it possible to configure the secondary routers' 2.5GHz band to be extensions of the main router's 2.5GHz band whilst keeping the respective 5GHz bands segregated?

I know of no such method, given the typical consumer grade wireless routers. Perhaps there is a way and perhaps other gurus will chime in here to inform us, but I doubt it is possible or feasible with the gear you and I buy for home use. You could, however, have different SSIDs for the 2.4 and 5 gHz bands. Depending on the router, you may even be able to have seperate passwords. My Archer supports this.

I’d probably turn off the 2.4 gHz band in the individual routers and turn off the 5 gHz band in the master router. Then use the master router’s 2.4 gHz wireless when you are all in, for example, the common area such as the kitchen or patio.

> D.) Stupid question: Is configuring all four routers' 2.5GHz band to the same SSID and password equivalent to extending the networks?

No, but it’s the equivalent of asking for trouble. Many Linux drivers and Network Manager will constantly attempt to roam and drop and reconnect. That’s why I suggested different SSIDs and passwords.

> E.) Stupider question: if a router is configured as a wireless AP, can a hardwired laptop connected to one of its ports still get network connection?

Certainly. I'd recommend it, in fact, as ethernet is usually faster and certainly more secure.

As for heavy bandwidth, you will most likely be limited by the ISP, not the router. My Archer C7 has no trouble dispensing gigabit internet to 8-10 devices.

---

### Post by bosscheesemo on 2018-03-28
Thanks for the reply and information. It's very useful and it helps very  much. Especially knowing that setting two routers to the same SSID is trouble I think I ran across exactly what you described with my phone seeming to drop connection frequently. 

Your assumption is correct that these two routers are connected via ethernet. So with all the WiFi questions answered, do the IP settings all check out for our intended network? I'm especially in the dark about subnets.Hell for all I know maybe I'm going off on this subnet business unnecessarily. Will a 192.168.2.1/24 address have privacy from a 192.168.3.1/24 address? If not, how to I set that up?

---

### Post by chili555 on 2018-03-28
> Will a 192.168.2.1/[COLOR="#FF0000"]24[/COLOR] address have privacy from a 192.168.3.1/[COLOR="#FF0000"]24[/COLOR] address? Entirely.

Since you already have set up one segment, I assume you are already aware that the *WAN* address for each of the subsidiary routers is 192.168.1.x and the gateway is 192.168.1.1. I suggest that they use static IPs outside the range of the DHCP server in the main router. Perhaps 192.168.2.1 (the LAN address) takes a LAN address of 192.168.1.102; and then 192.168.3.1 gets a LAN address of 192.168.1.103, etc. 

In other words: Secondary router 192.168.2.1
------------------------------------------------------------
WAN addresses: 192.168.1.102, 255.255.255.0, 192.168.1.1
LAN addresses: DHCP range 192.168.2.2 to 192.168.2.51, 255.255.255.0, 192.168.2.1
DNS 8.8.8.8, 8.8.4.4

^^ Rinse, repeat.

Finally, to prevent mischief and mysterious midnight changes to the topology, I'd use a difficult to guess usernames (not cheesemo!) and a strong passwords on all of the routers.

---

