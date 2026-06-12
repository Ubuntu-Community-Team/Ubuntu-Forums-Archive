---
title: "Some help pls...N/Wing."
date: 2009-10-14
forum: New to Ubuntu
---

### Post by nothingman02 on 2009-10-14
OK...have taken a round robin approach to the field of computer science in general and Linux in particular. I am from a diff. background and have recently made a change to computers. 
So first, I leanrt the basics of h/w and followed that with the basics of OS. Then I touched upon the basics of Linux and its filesystems etc and now am studying the basics of N/W. After that, itsgonna be 'linux internals' following which will be some more revision and  then RHCT training.

SO right now while studying N/Wing, I have this stupid doubt - I cant figure it out. Whats the need for a modem when we have a router?
I mean, is a modem required to connect a LAN to a WAN? 
A modem transmits analog signals. What does the router(without a builtin modem) transmit/forward? Analog signlas as well? If so, given the additional capabilities of a router, whats the need for a modem at all? 
Or is it that a router can only transmit data because its got a built in modem?

NOt sure if this is the right forum but hope to receive some help. Thanks.

---

### Post by cariboo on 2009-10-14
Yes a modem is needed to connected to a WAN. A router provides several things, it routes the signal to the computers on the network, it provides network addresses, and in most cases the router also provides a firewall.

---

### Post by nothingman02 on 2009-10-14
hi and thanks for the reply.

I understand that a router can perform lots more additional functions. But lets ignore that and look at the similarity. What are the similarities between a router and a modem?

If both a router and modem can transmit data, whats the need for a modem?

---

### Post by dearingj on 2009-10-14
I think to answer that question accurately, one should define what exactly a modem is. Strictly speaking, a modem (using the definition I learned in my Cisco networking classes) is a device which converts digital data into sound ([modulate]("http://en.wiktionary.org/wiki/modulate")) and sound into data ([demodulate]("http://en.wiktionary.org/wiki/demodulate")), hence the term 'mo-dem'. Those aren't too common any more, but in the '90s they were a very common way to connect to the Internet because they could transmit this sound over a normal telephone line. The more common use of the word 'modem' refers to any device which is on the border between a small local network and the wider Internet. The point, I believe, of a modem by this more common definition, is to provide transparency so that the devices on your network don't have to be specifically designed and configured to use whatever type of Internet connection you have. Cable Internet connections work differently than DSL, which work differently than fiber-optic, etc., but thanks to modems, your computer or router can connect to any of them using one standard interface.


Edit: You might want to edit the title of this thread to something a little more clear. When I first clicked on it, I thought N/Wing probably referred to some new flight simulator :)

---

### Post by mcduck on 2009-10-14
> **nothingman02 said:**
> hi and thanks for the reply.

I understand that a router can perform lots more additional functions. But lets ignore that and look at the similarity. What are the similarities between a router and a modem?

If both a router and modem can transmit data, whats the need for a modem?
There are no similarities between the two.

A modem is what handles your internet connection, converting the network traffic to signals for phone network, DSL or cable, or whatever connection you have. So a modem takes data from one network interface and converts it into different form to another interface.

A router simply separates two networks and routes traffic between them. A basic router only as two network prts, one for the local network and one for wide-area network.

Most consumer-grade routers are actually router+switch combinations, so in addition to separating the wide-area network from your local network they also manage the connections between different computers, directing traffic from one computer to other and from computers to the internet.

So if you only have one computer you can simply use a modem. If you have many computers and need to have them all connected to Internet, and also need to be able to send data between the computers, you also need a router & switch.

..then there are bridges (connecting two networks without separating them like router does), and repeaters (used to allow longer distance connections without signal loss), and hubs (kind of the same as switches, but sending all data to every port instead of only between the intended sender & receiver like a switch does).. I could actually explain all this stuff pretty well with a pen and some paper, but doing it with text is quite hard.. :D

---

### Post by nothingman02 on 2009-10-14
Hmm...first of all thanks for all the replies.

Heres my understanding and please let me know where im wrong...

1) LANs are connected to WANs through - telephone wires, DSL, cables, satellites, fiber optics etc. usually over a long distance through which a digital signal will not carry. Hence a modem is used to convert the digital signal to an analog one to send it out to the www. There are appropriate modems such as DSL modem, cable modem, satellite modem, fiber optic modem etc. 
2) Also a router cannot handle analog signals and  simply transmits/forwards DIGITAL data within a LAN. That is, the digital data coming out from the n/w card on the PC is forwarded by the router within its network in the LAN or out of its network to another router in the LAN or simply to the Gateway. The gateway is noting but a router+modem. Here the digital signal is converted to an analog one and sent out to the WAN, say an ISP. The ISP has another gateway (modem) to receive this analog signal and converts it into a digital signal and forwards it appropriately within its network through  the subsequent nodes. 

So within a LAN, repeaters, routers, hubs, switches, bridges etc will do and no signal conversion is required. But going out of the LAN  an appropriate modem is requried to convert and carry the analog signal to he ISP. 

Please let me know if the above is correct.

---

### Post by BQAggie2006 on 2009-10-14
You got most of that correct except for a few details, mainly around the modem part. Back in the 90's, when dial-up connections were more common, modems were true modems, meaning they converted communications from digital to analog and vice versa because telecommunication networks (i.e. phone company) were analog, not because of distance. Digital networks are actually better over long distance because there is less "noise" from repeating a digital signal compared to repeating an analog signal... if I remember correctly.

However, because more communications networks are becoming digital (i.e. cable company offering internet and phone companies offering fiber to the prem), a "modem" doesn't necessarily convert communications from digital to analog anymore, but merely acts as a gateway between the WAN and your LAN.

Take for example a cable modem. Standard LAN technology these days is the ethernet protocol over CAT5,5e,6 cabling. However, the cable coming into your home comes through on coax cabling and might even use a different protocol than ethernet. Therefore, the modem converts the digital signal from one physical medium and possibly protocol to another. This is why a cable modem isn't a true modem since it' doesn't modulate or de-modulate.

Check out the OSI Model for a basic understanding of networking.

---

### Post by nothingman02 on 2009-10-14
Hi BQAggie, thanks for the reply.

A couple of doubts here. 

If data transmission (throughout the internet) is digital, whats the need for a modem at all? It seems like it is for protocol conversion. Wouldnt a router accomplish that?

WIthin a LAN, if the ethernet protocol is replaced with a token ring, wouldnt a router handle this change in protocol? Likewise, externally, if the LAN is connected to the ISP through a fiberoptic cable isntead of a coaxial cable, wouldnt a router/gateway handle the change in medium and protocol? 

Thanks again to everybody for the patient replies. Im new to this field and all the help is appreciated.

---

### Post by BQAggie2006 on 2009-10-14
> If data transmission (throughout the internet) is digital, whats the need for a modem at all? It seems like it is for protocol conversion. Wouldnt a router accomplish that?True modems (devices that modulate and de-modulate digital data over analog signal) are still in use today in DSL and dial-up environments. What I was trying to get at was the fact that a lot of devices that are referred to today as modems (such as my cable modem example), are not true modems, but are gateways that convert protocol and network medium from one network to another (i.e. cable company's coax to home net CAT5). 

It's been a while since I took my telecomm class in college, but if I remember correctly, the basic differences between the main networking devices are:

[LIST]
[*]A gateway is a networking device that communicates between networks of different protocols and/or network mediums
[*]A router can convert between mediums (say a fiber-interconnect between routers or ISP to CAT5 or CAT5 to WiFi), but cannot convert protocols
[*]A switch cannot convert between mediums or protocols
[*]Hubs cannot convert between mediums or protocols and cannot switch packets, packets are broadcast to all segments
[/LIST]
Like I said, it's been a while, so someone please correct me if this isn't true.

---

### Post by niteshifter on 2009-10-14
> **cariboo907 said:**
> Yes a modem is needed to connected to a WAN. A router provides several things, it routes the signal to the computers on the network, it provides network addresses, and in most cases the router also provides a firewall.

Ah ... not really. For personal (homes) and many a small business the above is true. 

For many businesses (and a few homes) the LAN - WAN "connection" is via a gateway / router / switch, these can be separate devices or via a single device that incorporates all three functions. Or even with "modem-like" capabilites like "bridging" between copper media LAN to-from fiber media link to WAN provider.

---

### Post by mcduck on 2009-10-15
> **niteshifter said:**
> Ah ... not really. For personal (homes) and many a small business the above is true. 

For many businesses (and a few homes) the LAN - WAN "connection" is via a gateway / router / switch, these can be separate devices or via a single device that incorporates all three functions. Or even with "modem-like" capabilites like "bridging" between copper media LAN to-from fiber media link to WAN provider.

+1 for this.

Like I said, a router can actually be very simple device (at least it looks very simple ;)), and only handles the separation of networks and conversion of network addresses between them. A basic router only has two ports, one for each network it's connected to. (Actually it's even possible to have a router with only one port)

So a router won't even allow you to connect multiple machines into same network. You need a switch or a hub to do that. But routers are often combined together with a switch to provide both functionalities.

---

### Post by nothingman02 on 2009-10-15
HI guys,
Thanks for the replies and information. 

Im almost there and just a few more question to put things together.

1) If both transmit data digitally, whats the difference in functionality between a router and a modem. Say a cable modem. 

In other words, if a router can route and transmit digital data between different media (copper and fiber optic) and also handle the changes in protocols then;
   a) whats exactly is the modem doing? 
   b) if its the case that the modem is doing the actual protocol conversions and handling the difference in media   (copper and fiber optics etc), then how does the router transmit data within the LAN? Dont we need a modem with every router in a Network. Within a LAN for instance. 

THanks again for your patience. Im learning and working hard and getting somewhere thanks to the help in these forums. I will have my RHCT training starting nov 9 - 21st on which day is my exam and because of my lack of experiance and education, I am studyign hard now and trying to learn as much as I can.

---

### Post by mcduck on 2009-10-15
Since you are familiar with the way how token ring works, I suppose you also no how basic Ethernet works (all packets being broadcasted to every machine in the network).

The main purpose of a router is to stop these broadcast packets from traveling freely to other networks, instead only allowing those packets to travel from one network to other that are actually intended to do so.

If the router also handles some kind of protocol conversion I'd actually call it router/modem combination, instead of just a router.

Also note that the devices called modems actually require lots extra functionality, for example a cable modem will have to do all kinds of scanning, frequency switching, handshakes and other stuff to create the connection to the cable network. So while the connection might be digital, it's still very different from the local network connection.

A router that has, say, optical and RJ-45 ports would still be using the same protocols for both connections.

It's really a very simple thing, but what makes it so complicated s the fact that most devices actually combine a router with some other type of device.

---

### Post by nothingman02 on 2009-10-15
HI and thanks for the reply.

Let me take an example and then I promise I'll move on.. :)

Suppose theres somehow a LAN up in the hills of remote country Alabama. Suppose there are two n/ws in that  LAN. 1 is ethernet and 2 is token ring. A router (G) connects these two n/ws to the ISP through a satellite and hence there is also a satellite modem here. 

Now each of these n/ws is further divided in 2 smaller sub-networks each. Router 1 connecting A and B in n/w 1 and likewise, Router 2 connecting C and D in n/w 2.
---------------------------------------------------------------------------------------------------
Now,
IN the ethernet n/w 1, all the PCs should have ethernet n/w cards installed in them and the cabling connecting these PCs to the routers A and B are all ethernet cables. Since the media are all pertaining to the same technology (CAT 5 cabling) and (ethernet NICs), there is  NO MODEM REQUIRED. Am I correct? There is no protocol conversion required and a simple router/switch or a hub will suffice to handle these subnets A  and B. The router 1 will simply route data between its subnets A and B without any problems. 
Now, if we introduce a change in media by attaching token ring n/w 2 to the router G and an ethernet node in 1A wants to communicate with a roken ring node in 2D, will the router G handle the changes in terms of cabling, token ring NICs (in all the n/w2 nodes) and protocols or is a modem required as well?

If yes, then I can understand why a modem is required to connect a LAN to a WAN. 
If no, then it means that a router can handle all differences in protocols and  media and there seems to be no need for a modem.

Sorry for dragging on this subject. I hope I'll get it this time...and thanks for the patience..:)

---

### Post by mcduck on 2009-10-15
Yes, there would be no need for modems inside networks 1 and 2. Routers and switches would be able to handle the subnets ( a switch or a hub in each subnet to connect the machines together, and a router to separate the two subnets from each other), but wouldn't be able to handle the connection between network1 and network2 since they use different protocols and mediums.

I suppose you could call the device connecting those different types of networks a modem, at least in the same sense as cable and DSL modems are "modems" (note that they are not actually modulator/demodulators so they are not modems in the original meaning of the word) "Adapter" would be a better term, but the "modem" is commonly used for this kind of devices since that's something people were already familiar with when broadband technologies became available for consumers.

The main point is that these devices operate on different layers of networking, routers operate on [network layer]("http://en.wikipedia.org/wiki/Network_Layer"), while the "modems" work on [physical layer]("http://en.wikipedia.org/wiki/Physical_Layer") of the [OSI model]("http://en.wikipedia.org/wiki/OSI_model").

---

### Post by nothingman02 on 2009-10-19
HI and thanks again for the reply. 

I think ive saturated my head with tons of info. I think im getting a picture so let me explain my understanding. Would appreciate it if you would let me know if I am correct in my understanding. 

---------------------------------
LANs and WANs use different protocols/technologies such as;
Ethernet
Token Ring
ATM
other
-----------
X.25
Frame Relay
ATM
other
------------------------------------------------
Now, 
1) the** PHYSICAL TOPOLOGY**  used in LANs and WANs is completely **DEPENDENT** upon  the technology/protocol.
2) The **PHYSICAL MEDIA** used in LANs and WANs is completely **INDEPENDENT** upon the technology/protocols. 

Am I correct?

For instance, ethernet differs from ATM and Token ring in its framEs, encapsulation, and transmission/forwarding methodology. Ethernet broadcasts to every node and hence has to be connected in a BUS. Switched ethernet has ofcourse enabled a Star configuration.

So when designing a Network topolgy, one has to keep in mind the technology being employed in the TCP/IP. 
But** need not worry** about anything when selecting the transmission media such as cabling (coaxial or fiber optic or wireless) or equipment (routers or modems or switcheson etc)

Am I correct? If so, it would bring me to my original question of whats the need for the modem when a router is indepedent of the physical media and will transmit nevertheless.
If I am wrong, then every switch, hub, router on the LAN and WAN should have an appropriate interface for an appropriate type of cable (coaxial, fiber optic, wireless etc) shouldnt it? For instance, an edge router uses an appropriate interface (appropriate modem) to connect via satellite, cable, fiber optic, DSL etc..

Thanks again for your time and patience. Hope I get to move on this time..

---

