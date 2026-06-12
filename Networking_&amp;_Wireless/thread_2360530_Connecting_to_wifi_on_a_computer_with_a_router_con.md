---
title: "Connecting to wifi on a computer with a router connecting to another?"
date: 2017-05-05
forum: Networking &amp; Wireless
---

### Post by pandoragami on 2017-05-05
Basically there are two computers with one wifi and a router connecting both computers. I could get the computers to ping each other through the router but I cannot figure out how to
connect one computer (B) to the wifi through the router which is connected to the other computer (A) which has wifi to the internet.


Here's a simple drawing of the problem where computer B is unable to connect to wifi.

...../router\..../Wifi with internet
.../..............\ /
B...............A

What I've done so far is try to setup the connections manually to the router for A and B. I've also tried to setup A as "shared to others" and B manually.


The ip address for the router is 192.168.1.1 and the ip subnet mask is 24.


For the wifi the ip is 192.168.0.13, broadcast address 192.168.0.255, Subnet Mask 24, Default Route 192.168.0.1, Primary DNS 75.75.75.75 and Secondary DNS 75.75.76.76. 


I could get the two computers to ping each other if I set them manually both to an address
range of 192.168.1.# but if I set computer A to "share with others" then I get an ip that 
starts with 10.#.#.# and this conflicts with the router (I assume I need to set it to a static address
with 10.#.#.# ).  


I've looked around the internet for threads on this topic but all of them sort of match my problem and none of them solve much for me which is why I started this thread.

---

### Post by TheFu on 2017-05-05
Don't use the router as a router. Use it as a LAN switch. Do NOT connect the WAN port. Do not use DHCP from it. Do not use DNS from it. Make the wifi-capable machine the router. Follow instructions for that.  Make certain that the wifi connection is the default route for any traffic that isn't on the same subnet, so all internet traffic goes out over it.

[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) should help, just be certain the wifi device is the WAN side in all your settings.

---

### Post by pandoragami on 2017-05-05
> **TheFu said:**
> Don't use the router as a router. Use it as a LAN switch. Do NOT connect the WAN port. Do not use DHCP from it. Do not use DNS from it. Make the wifi-capable machine the router. Follow instructions for that.  Make certain that the wifi connection is the default route for any traffic that isn't on the same subnet, so all internet traffic goes out over it.

[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) should help, just be certain the wifi device is the WAN side in all your settings.

Hey! Thanks for replying, anyways, nope didn't use the WAN. I figured as much and DHCP just goes wonkers making the whole network not even allow a ping to get though. I figured that starting with the basics would work and then building up from there. I mean the basics by pinging two computers and seeing if that works. The parts I'm having difficulty with is setting the DNS on computer A connected to the wifi and the router. I'm not sure which IP address to use from the wifi connection for the Gateway and the DNS servers settings for the wired connection on computer A under the IPv4 (this is so that the router can send computer B's packets through the router onto A).

In other words I'm looking at the  wired network settings on computer A under the IPv4 where I set the address of the computer manually as 192.168.1.2 (the router is 192.168.1.1) and what IP address would I use for the Gateway and the DNS servers. I'm guessing it would be one of the addresses from the wifi connection but not sure which. 

Another problem I noticed was that my internet doesn't work if I have both the hard wired connection and wifi running on computer A, well except google does load but not any links from a search. If I disable the hard wire connection then it works normally???

---

### Post by TheFu on 2017-05-06
When I say "don't use", I mean do not configure AND don't use.  You need to disable all those things on the router. It needs to be a dumb switch. Nothing it provides should be used.  No IPs, no dhcp, no subnetting, no DNS. Nothing. It would be better if you put a dumb switch there.  This would simplify the setup to 2 computers. Did you **enable routing** on the computer with wifi? That's a system.  I don't think "share with others" is sufficient to make a computer into a router. There are system config files that need to be manually modified to work. You didn't mention that, so I'm concerned.

BTW, from a security standpoint, you'll need to make this computer into a firewall with firewall rules.

The wifi IP should be provided by the ISP. It should be a public IP, not some internal LAN, non-routeable IP.
A-wifi=50.x.x.x (something provided by the ISP)
A-LAN=10.x.y.1/24
B-LAN=10.x.y.2/24
The gateway should be A-LAN from B-LAN.

I would avoid all the 192.168.x.x addresses. There are a number of reasons for this. Confusion. Running a VPN later will need some other subnetting to avoid conflicts. You want your internal LAN subnet to be _different_ from any you might be on in a cafe, library, hotel, or at any company.  I use the 172.22.x.x/24 subnet for my LAN. This is a less popular non-routeable internal subnet.

If this doesn't help and just confuses you more, I'm afraid someone else will need to try to explain it more clearly. It is my failure.

---

### Post by pandoragami on 2017-05-06
> **TheFu said:**
> When I say "don't use", I mean do not configure AND don't use.  You need to disable all those things on the router. It needs to be a dumb switch. Nothing it provides should be used.  No IPs, no dhcp, no subnetting, no DNS. Nothing. It would be better if you put a dumb switch there.  This would simplify the setup to 2 computers. Did you **enable routing** on the computer with wifi? That's a system.  I don't think "share with others" is sufficient to make a computer into a router. There are system config files that need to be manually modified to work. You didn't mention that, so I'm concerned.

BTW, from a security standpoint, you'll need to make this computer into a firewall with firewall rules.

The wifi IP should be provided by the ISP. It should be a public IP, not some internal LAN, non-routeable IP.
A-wifi=50.x.x.x (something provided by the ISP)
A-LAN=10.x.y.1/24
B-LAN=10.x.y.2/24
The gateway should be A-LAN from B-LAN.

I would avoid all the 192.168.x.x addresses. There are a number of reasons for this. Confusion. Running a VPN later will need some other subnetting to avoid conflicts. You want your internal LAN subnet to be _different_ from any you might be on in a cafe, library, hotel, or at any company.  I use the 172.22.x.x/24 subnet for my LAN. This is a less popular non-routeable internal subnet.

If this doesn't help and just confuses you more, I'm afraid someone else will need to try to explain it more clearly. It is my failure.


No confusion; you make sense, a lot actually! It's more about not knowing how certain config files are used in the first place. Another question is what do you mean by "The wifi IP should be provided by the ISP. ". Say that I can get the address to the outside world, where would I add that because the wifi just connects to a modem and that connects to the internet. I can't really change that part. What's a non-routeable IP? 

Thanks a lot for the suggestions so far. I guess this will take some time to resolve. It's not super important but knowing how this stuff works is something that should be part of someones experience in networking.

---

### Post by TheFu on 2017-05-06
Is your diagram correct?  Modem? Huh? What?  That's the first time you mentioned any modem.

---

### Post by pandoragami on 2017-05-06
> **TheFu said:**
> Is your diagram correct?  Modem? Huh? What?  That's the first time you mentioned any modem.


Right! Forgot to mention that the wifi connects to a broadband internet connection and the wifi is part of the LAN itself. The modem is the part that is the "DMZ". I suppose that would be the main router then and computer A connected to the wifi and the router ( between A and B) are all part of the LAN. This is why I'm not sure that the computer called A could ever be a router like you mentioned and should be seen instead as part of the LAN ( in my opinion) while the modem connecting the broadband connection should be the router (dmz).

---

