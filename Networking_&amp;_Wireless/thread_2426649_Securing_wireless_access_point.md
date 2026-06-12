---
title: "Securing wireless access point"
date: 2019-09-11
forum: Networking &amp; Wireless
---

### Post by aljames2 on 2019-09-11
At home I have 3 subnets:

1- LAN with PC & Server
2- Wireless Access Point dedicated for IoT devices to get out to the internet.  (Crap devices like game consoles, microwave, etc.)
3- Wireless Access Point for only internal access to the LAN via wireless laptops in the home.

All 3 subnets are behind a pfSense router.  Currently router blocks all inbound traffic on the WAN side.  Eventually, I’ll have to open a port for remote SSH.

Concern now is how to protect the LAN from attacks on #3 above.  The router should stop inbound traffic but just in case the AP was hacked somehow is my concern.  Wondering if I need some type of internal tunnel between the wireless laptops on the #3 subnet and the LAN?  Trying to figure out how to do this the right way.

---

### Post by TheFu on 2019-09-11
I use the ISP's gateway for all wifi networking and have it in bridge mode to pass the public IPs directly to my pfSense router.  All wifi is outside the pfSense and untrusted.  I don't trust any wifi security.

I keep my wifi AP separate from my WAN router.```

ISP-GW
&#9500;&#9472;&#9472; pfSense-router
&#9474;** &#9500;&#9472;&#9472; Wired-Desktops-LAN
&#9474;** &#9474;** &#9492;&#9472;&#9472; 172.22.21.x
&#9474;** &#9492;&#9472;&#9472; Wired-Service-LAN
&#9474;**     &#9492;&#9472;&#9472; 172.22.22.x
&#9492;&#9472;&#9472; WiFi-Guests
    &#9492;&#9472;&#9472; 10.1.10.x
```
Wifi guests have to use a VPN to gain access to the internal networks.

---

### Post by aljames2 on 2019-09-14
Would the VPN from guest wireless into the LAN be configured as a remote access VPN or a site to site?  

I would set up OpenVPN on the pfSense router.  I’ll need to change a few things but I could use my ISP gateway the same.  Currently pfSense is my edge router/firewall.

---

### Post by TheFu on 2019-09-14
I run openvpn on a VM on the Server LAN.  Site-to-site?  From android systems?  Nope.   I don't believe in having WAN routers do anything other than firewall and routing.  Plus, any system inside the protected LAN can directly access the wifi LAN. The ISP-GW does that automatically.  The ISP-GW is a small-biz Cisco router. Only my public IP subnet is passed through. Everything else about it seems to work like any other wifi router.

I use both my own VPN and a paid VPN from different devices for different reasons.  Just depends where I am in the world.

Complex code leads to configuration mistakes and bugs.  I spent too many years as a software developer and Unix admin and remote access "guy" to do anything different.  

There are lots of other things that people do with their routers that I would never do - like connect any storage to be shared to it.  That's just asking to be hacked.

BTW, my "desktop" wired LAN is extended using powerline ethernet between floors.  It isn't GigE, but I do see a solid 60Mbps connection, which is sufficient for a home PC in the den and running a projector with a Raspberry-Pi.  

There are lots of reasonable solutions. Mine is just one of them.  I've been deploying wifi solutions since the early 2000s for enterprises.  We always required a full VPN with 2FA to gain access to the corporate network if wifi is used.  

A few years ago, while at a security conference, my laptop got hacked over bluetooth.  That immediately ended all bluetooth use here.  Seems new hacks are being found for it all-the-time.  Don't trust any RF-based protocols to be secure.  Seriously. All of them can be hacked.

---

### Post by aljames2 on 2019-11-16
I have a Verizon gateway/router (G1100) that I do not use as it is not easily placed in bridge mode.  My pfsense router WAN is currently connected directly to my verizon service demarcation via ethernet.  So my pfsense is currently holding my public IP lease.

If I wanted to move my Ubiquity access point (wifi) outside my pfsense firewall/router, I am thinking I could use a consumer router in bridge mode to hang my AP off for physical separation.  I think this would be like TheFu’s diagram except I would be using a consumer router in bridge mode in place of the ISP gateway/router?

The problem I envision though is I use a Rasberry Pi to run the Unifi Controller which is required to operate my Access Point.  The controller must run on the same subnet as the Access Point. How can I achieve security of my Pi and AP when they would be placed outside my internal firewall?

---

### Post by TheFu on 2019-11-16
I don't often reply to 2 month old posts. Usually unsubscribe after a week or so.

UniFi Controller doesn't need to be on all the time, just during configuration changes.

Every Ubuquity AP I've seen can use a UniFi controller that is located anywhere networking allows connections.  People run them on AMZ-EC2, for example.

If the Verizon has more than 1 LAN port, why not just connect the AP into that?  Does it not provide a 10.x.x.x subnet?  How would that be any different then having any other device in bridge mode?

---

### Post by aljames2 on 2019-11-16
Sorry about the agedness of the thread, and thanks for seeing it again.

Verizon does not have a setting to put it into bridge mode.  It&#8217;s sort of a quasi-bridge mode that you mimic through adjusting a bunch of other settings as described here:  [https://www.flyn.org/notes/g1100-bridge/index.html](https://www.flyn.org/notes/g1100-bridge/index.html)

I may just give it a try as you suggest and see if it works.  I just don&#8217;t want to have two routers trying to do Nat.  Hopefully these crazy steps will actually put the thing in bridge mode.

---

### Post by SeijiSensei on 2019-11-16
I have two routers in series both doing NAT.  I've done so for years. In an earlier post, TheFu mentioned a couple of services that don't like this, but I don't use any of those. My primary line of defense is a long, complex passphrase.

---

