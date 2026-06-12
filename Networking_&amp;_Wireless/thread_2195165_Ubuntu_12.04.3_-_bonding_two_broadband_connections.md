---
title: "Ubuntu 12.04.3 - bonding two broadband connections pppoe&amp;static into 1 LAN"
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by gogoasha2001 on 2013-12-22
Hello everyone!

First of all i'd like to start with saying that i'm new to this community, although not completely new to Linux and/or Ubuntu. I have fiddled with several distros in the past, including Ubuntu, but in the past two years i've been out of the loop. So take it easy on me as i get acquainted again and i do hope you can help me out.

I currently have two broadband connections in my house, one is a 1Gbps PPPoE (dynaminc IP) and the other one is a 100Mbps (static IP), different providers. While i know there are other, simpler ways, to merge two connections, my goal is to do it with Ubuntu. I'm just tired of having to move around with an external HDD or USB memory from one computer to another to transfer large amounts of data when i have to. Simply put, i want to bond both broadband connections on linux, output it to my primary wireless router and have all my PCs & devices on 1 single LAN connection for easy sharing.

I have searched the web extensively for a way to do it and found some interesting articles that expain things like routing or teaming multiple connections/uplinks, but none of them actually taught me how to setup my network interfaces in Ubuntu so that both broadband connections can work simultaneously (i don't care about the speed, i care about redundancy and having 1 LAN for all PCs that could potentially access the internet even when 1 broadband connection is down).

I've managed to scrape off a PC to act as router/firewall/samba server for shares. I've got 3x 1G network cards. What i envision is this: 

```
#1 broadband (1Gbps) connection on eth1 + #2 broadband (100Mbps) connection on eth2 -> bonded on eth0 and sent to wireless router -> home PCs either through wires or wireless
```

Currently i'm stuck. I have all 3 network cards installed and working (hopefully), although i have not configured them yet and need to do so and test that they are working independently. Also, i am not sure how to set-up the #1 broadband connection to auto-connect a pppoe connection to my provider every time the server boots, and after doing so, how will that work (if even possible) considering it will have a different IP every time. Configuring the #2 broadband connection seems pretty straightforward considering it's a static IP given by my other ISP, although it's based on the MAC address of the router it currently uses, so i will have to clone the MAC address for eth2 to bring it up successfully. And lastly how will i merge the two interfaces into one and deliver the result to my home router so that all PCs/stations can access the internet? 

It is my understanding that i will have to build routes(?) and set-up some kind of load balancing? I would also like to setup a firewall and lastly, but that's the least of my concerns, a samba server to enable sharing and dumping for all clients in my house.

I know it seems alot to ask, but i'm not an advanced user and even though it's out of my league, I'm confident i can pull it off with your help. It's a project i've been considering for the better part of this year and i have finally managed to get all the hardware together and, most important, the free time (yay! for holidays) to implement it.

What say you? Care to help a fellow out of the dark?

Thanks a bunch for taking the time to read this!

---

### Post by houstonbofh on 2013-12-23
This is really a lot harder than you know.  I would just install pfSense on a spare box and use the dual wan functionality there.  It is FreeBSD, so you can poke around under the hood if you wish. But the key is, they have already done all the hard stuff, and it is tested and proven.

---

