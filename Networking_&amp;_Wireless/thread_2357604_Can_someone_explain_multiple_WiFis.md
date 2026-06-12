---
title: "Can someone explain multiple WiFis?"
date: 2017-04-04
forum: Networking &amp; Wireless
---

### Post by cleeve512 on 2017-04-04
I have 2 routers: the first (192.168.1.1) is connected to the internet and has cable & WiFi connections; the second (192.168.1.50 static) is connected by cable to the first and has WiFi plus some static cable connections. The 1st has DCHP enabled, the 2nd doesn't. Both have the same SSID. 
Question: is the 2nd WiFi connections considered to be part of the first and how are its IP addresses allocated?

---

### Post by izznogooood on 2017-04-04
This wont work.

You need to have the seccond router set up as an access point. The wired connections will sort it self out (since you have disabled the dhcp on the second router the ports will act as any normal switch), but two Wifi's with the same ID and no bridgemode is a recipe for disaster. 

You can read more about setting up access points here: [https://www.howtogeek.com/104469/how-to-extend-your-wi-fi-network-with-simple-access-points/](https://www.howtogeek.com/104469/how-to-extend-your-wi-fi-network-with-simple-access-points/)

---

### Post by cleeve512 on 2017-04-04
You are right --- it doesn't work. However, I read the link and it is exactly how I have it set up. I now accept that the IP addresses are all managed by R1 so there will be no conflict and it will see them all as the same WiFi network. Still, if the android is connected to WiFi-R2 and the Chromecast is connected to WiFi-R1 why can't I cast to the TV? It works if I reset the android to connect to R1.

---

### Post by izznogooood on 2017-04-04
Are you sure R2 is set up in Access Point mode?

---

### Post by cleeve512 on 2017-04-04
Yes, defo Access point.

---

### Post by izznogooood on 2017-04-04
Hm, very strange. Your second router is connected from the first in to the WAN port of the second i presume? I remember I had simuler issues with my chromecast. (5Ghz vs 2Ghz)...

I would do as the guide says and default the second router. Leave the dhcp on as the router will handle the routing between the subnets anyway...

When it comes to the chromecast i think I used settings to allow anyone "closeby" to be allowed to cast (You have to enter a pin once anyway).

---

### Post by SeijiSensei on 2017-04-04
I'm pretty sure the Chromecast device has to be on the same network as the casting device.

I have a separate router behind the one I got from my ISP.  I turned off wifi on the ISP's router and pass all traffic back to my own via Ethernet.  All my networked devices connect to my router and none to the ISP's.  My router also has an entirely separate network subnet from the one my ISP's router provides.

---

### Post by izznogooood on 2017-04-04
> **SeijiSensei said:**
> I'm pretty sure the Chromecast device has to be on the same network as the casting device.

I have a separate router behind the one I got from my ISP.  I turned off wifi on the ISP's router and pass all traffic back to my own via Ethernet.  All my networked devices connect to my router and none to the ISP's.  My router also has an entirely separate network subnet from the one my ISP's router provides.

Then you should put your ISP's router in Bridge mode.... Now you are double NATing which is slow and can cause all kinds of problems...

The chromecast is on the same network. ;)

---

### Post by SeijiSensei on 2017-04-04
NAT never seems to have any observable effect on the speed of traffic flows.  Nor have I ever had any problems with this arrangement over many years of employing this configuration.  I don't want to change settings on the ISP's router, and this way I don't have to.  

I don't know what your comment about Chromecast is supposed to mean.  The OP reports
> Still, if the android is connected to WiFi-R2 and the Chromecast is connected to WiFi-R1 why can't I cast to the TV? It works if I reset the android to connect to R1. 
which confirms my earlier observation that both devices need to connect to the same router for casting to work correctly.

---

### Post by izznogooood on 2017-04-04
Whatever floats your boat. What I ment is that his chromecast is technically on the same network, it just does not seam to get that. Like i said i had the same problem with a 2G/5G router.

---

### Post by SeijiSensei on 2017-04-04
His basic problem is that both routers are in the same IP subnet.  As I said, the only reliable solution is to have each router use a different subnet.  Otherwise traffic arriving at router A looking for a service on router B will not be routed properly.

---

### Post by cleeve512 on 2017-04-05
Thanks Guys, but you are losing me. Chromecast requires devices to be on  the same network so my question is: are R1 and R2 on the same network and if  not how to make them.
Some further info & answers: R2 does not  have a usable WAN input port (it's a telephone socket) so the R1-R2  connection is Ethernet port to Ethernet port. If I look at the WiFi station info on R1 I see all connected devices. However on R2 I see only the local WiFi devices. I don't know much about bridging but on R2 it says "Bridge restrict - Disabled". R1 is TL-WR841HP and R2 is TD-W8960N. I only use 2.4GHz. I can ping the WiFi printer on R1 from a Cable connected PC on R2. Finally (and hopefully not relevant) R1 is set as country = USA for a stronger signal (which doesn't reach the road or neighbours) and R2 is probably set as UK. Hope that helps.

---

### Post by SeijiSensei on 2017-04-05
Leave the router with the cable connector alone.  Plug the WAN port of the second router into one of the first router's LAN ports.  It should get a DHCP address from the cable router.  (You may want to make this a static address once things are working properly though it usually won't matter.)  Assign a different IP subnet to the second router.  If the first router distributes addresses in 192.168.1.0/24, have the second router use something like 192.168.50.0/24.  Turn off wifi on the cable router, and connect all devices wired or unwired to the second one.

---

### Post by cleeve512 on 2017-04-05
I don't understand. R2 has 4 Ethernet LAN ports and a telephone port (RJ11 ??) Which would normally be used for the broadband input. I can't connect this to a LAN on R1. R1 & R2 are connected using a LAN port of each. I was originally thinking that R2 is essentially just a switch.

---

### Post by SeijiSensei on 2017-04-05
> **cleeve512 said:**
> I have 2 routers: the first (192.168.1.1) is connected to the internet and has cable & WiFi connections; the second (192.168.1.50 static) is **connected by cable** to the first and has WiFi plus some static cable connections. The 1st has DCHP enabled, the 2nd doesn't. Both have the same SSID.
> **cleeve512 said:**
> I don't understand. R2 has 4 Ethernet LAN ports and a **telephone port (RJ11 ??)** Which would normally be used for the broadband input. I can't connect this to a LAN on R1. R1 & R2 are connected using a LAN port of each. I was originally thinking that R2 is essentially just a switch.

Usually when we see "cable" we think Ethernet, not a telephone line.  That has to be a pretty ancient device if it has no Ethernet WAN port.  (And yes, it's an "RJ-11" port.)  Designed for a DSL connection?

So why not just dispense with router 2 altogether?  What purpose does it serve?  If you want to expand the number of available Ethernet ports, then turn off its wifi radio and just use it as a switch as you appear to be doing now.

---

### Post by cleeve512 on 2017-04-05
The CABLE I talked about right from the start has always been a standard RJ45 Ethernet cable so there should have been no confusion. I wasn't even aware of the RJ11 "telephone socket" until this morning. So, I'm sorry if you think you were misled. It looks like it is possible to extend this network using the 2nd router as a LAN switch, but the WiFi aspect of the switch has limitations in being considered a separate network. Thanks for your help.

---

### Post by cariboo on 2017-04-06
I use two routers, one that does everything a router should, and the second one connected to the first via cable that runs as a wireless ap. According to it's manufacturer all I needed to do was set an ip address, and turn off all services and make sure the cable was connected to one of the LAN ports.

IP addresses are:

[LIST]
[*]192.168.0.1
[*]192.168.0.2
[/LIST]

---

### Post by cleeve512 on 2017-04-07
It sounds like you (cariboo) have the exact same setup as I have. You can move seamlessly with your iPad/android from router to the other maintaining the same IP address. So what is your experience in controlling a WiFi printer or Chromecast on one router from your phone connected to the other router. I'm beginning to believe they are separate networks in a sense but need to understand exactly what is happening. Having read some instructions regarding Linksys they insist on turning off the WiFi on the second router --- there must be some reason for that.

---

### Post by izznogooood on 2017-04-07
Could you please:
Explain what it is you want to achieve?
Then if you could provide the Make and Model of your Routers?

---

### Post by cleeve512 on 2017-04-07
The routers are both TP-Link and the models as I stated in my first post on this page 2. It seems easy to add an additional router to extend a LAN network. There are lots of sites that explain how to connect them with an Ethernet cable such that the 2nd acts as a switch on the same network. However in all the examples i found, it seems that this second router is limited to cable connections only. I have mine working with WiFi connection also, but I think the WiFi is not really seen as the same network in the way that the cable connections are. I want to understand why the WiFi is seen as a different network.

---

