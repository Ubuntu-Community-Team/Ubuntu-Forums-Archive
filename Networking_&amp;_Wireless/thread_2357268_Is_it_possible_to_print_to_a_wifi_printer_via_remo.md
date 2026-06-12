---
title: "Is it possible to print to a wifi printer via remote wifi switch - closed."
date: 2017-03-31
forum: Networking &amp; Wireless
---

### Post by cleeve512 on 2017-03-31
My main office has a WiFi printer (Epson Stylus Photo PX830FWD), a PC and a broadband WiFi/LAN router (TP-Link). The printer IP address is 192.168.1.90 (static). I can print OK from the local PC. Another office (200yds away) is connected to the main router by LAN to another WiFi/LAN router which is set-up as a simple switch. The remote office PC (Ubuntu 16.04) is connected by Ethernet to the local "switch".  I'm having problems printing from the remote office to the main office printer. Is it because both routers have WiFi networks?  BTW both "routers" have the same SSID so movement between the two offices is seamless.

---

### Post by Elkenfugel on 2017-04-01
Hello cleeve512,

I think this is because your 'remote' office pc is connecting to your network via the Ethernet switch and not the wi-fi. Have you tried looking at the IP addresses for the computers to ensure they are on the same subnet (i.e. 192.168.1.XXX)?

here is a link to instructions on checking IP addresses in Ubuntu. 

or you can type

```
ifconfig
```

in a terminal and read the "inet addr:" value

---

### Post by cleeve512 on 2017-04-02
Yes, everything is on the same 192.168.1.xxx subnet. In printer properties it says for the last job "stopped Rendering completed". However the printer is flagged as "paused" (even though it isn't. On the Policies page the "Enabled" box will not stay checked and it says "Not published See server settings". Any other ideas of what I'm doing wrong?

---

### Post by SeijiSensei on 2017-04-02
I would have put both offices on separate subnets and handled connections between them via routing.  Can machines in the remote office see machines in the main office?  Unless the 192.168.1 network is subnetted into, say, a /25, routing is going to be problematic.

The "seamless" feature you described could equally well be handled by two routers with different SSIDs.  If I move from one wifi network to another with my smartphone, it moves my connection with it.

---

### Post by cleeve512 on 2017-04-03
> **SeijiSensei said:**
> I would have put both offices on separate subnets and handled connections between them via routing.  Can machines in the remote office see machines in the main office?  Unless the 192.168.1 network is subnetted into, say, a /25, routing is going to be problematic.

The "seamless" feature you described could equally well be handled by two routers with different SSIDs.  If I move from one wifi network to another with my smartphone, it moves my connection with it.

I think you may have confirmed my suspicion about WiFi networks. If I take my android tablet to the remote office it switches to that WiFi, although it keeps the same IP address; however when I return to the main office (home) it often stays connected to the remote WiFi as it is only 100yds away. I have noticed that casting to Googlechromecast doesn't work unless I manually force the tablet WiFi to connect to the main office (to which the Google cast device is connected). Clearly, there is dome disconnect between the WiFi networks.
So, even though the PC at the remote office is connected by Ethernet cable I'm thinking that the printer sees it as on a different WiFi network and therefore will not connect.
Is that right?
BTW on your system can you be watching a video on your smartphone via one router and transfer to the other router without a glitch? or do you need to reconnect the video?

---

### Post by SeijiSensei on 2017-04-03
Depends on where I'm located.  I don't have this arrangement myself, but I have a friend with two separate routers in adjacent buildings. My phone sees both of them and chooses the one with the strongest signal. However they have entirely separate SSIDs and are not interconnected in any way.  

For the case you described, I'd set up two routers with different SSIDs and separate local networks.  Both routers would need static routes to the other network.   So on the router with MainOffice as its SSID, I might use 192.168.50.0/24, and on the second router 192.168.60.0/24.  Then each router would need a static route to the other network via the other office's router.

I have a client with satellite offices.  Each has a separate /24 network with appropriate interconnections and routing.  All Internet-bound traffic is eventually routed to the border router I maintain that interconnects the offices and the Internet.

As I asked, can you ping machines in one office from machines in the other? If not, then you won't be able to print.  Here's what I suspect is happening.  Suppose the printer is at 192.168.1.5.  If you're on the same router as the printer, that router will know where to send print jobs.  But if you're in the other building on the other router, it will look to its own local network for 192.168.1.5 because it doesn't know how to route traffic to the main office.

---

### Post by cleeve512 on 2017-04-03
Thanks. I can ping the printer from the remote PC. I'm still confused if it considers both WiFi's as a single composite network. The cable connections are all static. The WiFi connections are DCHP (except the printer which is static. The Chromecast experience suggests they are two networks (although I think the DCHP is all controlled by the main router).  
I know that I could have two separate SSIDs as I had this originally. I need to remember why I switched to the same SSID --- there was a good reason.

---

### Post by cleeve512 on 2017-04-04
CLOSED. Thanks to those who replied and clarified my thinking on this issue. I am closing this thread and reposting with a focus on how the WiFis are configured.

---

