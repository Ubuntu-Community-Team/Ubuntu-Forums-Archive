---
title: "Questions about LAN &amp; WLAN setup"
date: 2018-02-07
forum: Networking &amp; Wireless
---

### Post by zkab on 2018-02-07
Here is my environment:

1) Firewall (Ipfire) has two NIC:s
   RED   -> Internet
   GREEN -> switch -> LAN
2) Now I want to add a WiFi network (mesh network)

How should that be connected ?
My idea is to connect one of the mesh point to the switch and then all WiFi users can access Internet.
But on the other hand WiFi users then have access to my LAN ... which is not what I want.
Also I cannot control the WiFi users via firewall rules.
Is there away to manage the WiFi users and only allow some of them to access the LAN and others not ?
Also I want a secure connection between LAN & WLAN users without any doors open.
I know this is not a Ubuntu issue but I guess there are many in this forum who have solved this in a better way than me ...

---

### Post by TheFu on 2018-02-07
Add another NIC, connect a wifi AP to that.  Ubiquiti can "daisey-chain" APs. Put the APs on a different subnet and firewall that interface.

OR

Get a some Ubiquiti APs, connect it/them to the Internet device and connect your IPfire device to the internet device on a different port.  My ISP provides a router that has 4 LAN ports and dhcp for the 10.0.1.x/24 subnet.  My router gets the public IP (I have a public /29 static).  All wifi is on the outside of my subnet and access for approved wifi devices is only available when using a VPN into the internal network.  This solves all sorts of security issues, since putting the IoT stuff (Roku, Chromecast, TV, BR, VoIP ATA, gaming systems, fridge, toaster, amazon buttons, etc.) on the outside reduces risks to your data too. Basically, wifi is a guest-network.

It really comes down to how you want to secure the network and how much you don't want casual wifi users to have access to internal stuff.

Before I had a full VPN working, putting the wifi external was something I only did when house guests visited.  With the VPN working, android devices and my laptop when on travel has full access to the internal network. It is very convenient, especially for android.  The laptop always had ssh access via ssh-keys to the LAN.

I posted a diagram on a public website [http://www.ratemynetworkdiagram.com/](http://www.ratemynetworkdiagram.com/) years ago, but it went under and all the 10,000+ network diagrams on that site have been lost.  Maybe the wayback machine has some of them?  Nope. 302 errors. That's the danger of trusting the cloud with our data. It can disappear. ;(

If you don't have a campus, a Ubiquiti LR wifi-AP can probably cover your house nicely.  [https://www.amazon.com/Ubiquiti-Unifi-Ap-AC-Long-Range/dp/B015PRCBBI](https://www.amazon.com/Ubiquiti-Unifi-Ap-AC-Long-Range/dp/B015PRCBBI) it really is designed for long range applications.  Check out some youtube videos on this version. Saw one where a guy was in the country and had the entire house covered and about an acre surrounding it too. Of course the building materials will matter greatly for coverage.

The great things about ubiquiti APs - they use PoE, so the antenna placement doesn't need to be near an outlet.  My router is in an upstairs corner of the house, but the AP is connected through a CAT5e cable through the attic to the center of the house. Looks like a smoke detector mounted to the ceiling.  I don't have the LR version. Didn't need it.  Coverage reaches all the house, garage and nearly to the fence in the back yard.  I stream movies on a tablet to the fire pit over wifi.  If required, I could add another AP from the end of the other one and run more CAT5e elsewhere to get more coverage.  Comparing other SOHO APs just isn't possible after seeing Ubiquiti stuff work. Highly recommended, especially over any big-box store routers/APs you might consider.

---

### Post by zkab on 2018-02-08
> **TheFu said:**
> Add another NIC, connect a wifi AP to that.  Ubiquiti can "daisey-chain" APs. Put the APs on a different subnet and firewall that interface.
I guess that is the way to go ... I am not going to buy Ubiquiti equipment since I already have Google WiFi.
When I create a different subnet for the WiFi network and firewall it ... how can I allow some WiFi users still access my internal LAN ?

---

### Post by TheFu on 2018-02-08
> **zkab said:**
> I guess that is the way to go ... I am not going to buy Ubiquiti equipment since I already have Google WiFi.
When I create a different subnet for the WiFi network and firewall it ... how can I allow some WiFi users still access my internal LAN ?
VPN.  That's the only way if you want device/user-level access controls.

Is that google-thing placed where you need it? Central?

---

### Post by zkab on 2018-02-09
Please explain where do I setup the VPN ... I am not sure about what you mean.
Right now I have 'ipfire' as my firewall with 3 NIC:s RED and GREEN and PURPLE

Internet -> RED -> Ipfire -> GREEN -> switch -> LAN users
Google WiFi  ->  PURPLE -> Ipfire -> Google WiFi users

Ipfire can also act as a VPN server but where do setup the VPN connection - should WiFi users talk to the VPN server ?

---

### Post by TheFu on 2018-02-09
I wouldn't put a VPN on a router. Routers should do routing and blocking, not be all-in-one devices, IMHO.  Wouldn't want to undermine the router security or the VPN security by mixing functions in that way.  

My VPN runs on a server-LAN, inside a VM.  The outside world gets 1 port to the VPN server - well, that isn't really true.  I allow 1 UDP port and 1 TCP port.  UDP is more efficient for VPNs, but many hotels, libraries, and other get-in-my-way networks block all UDP, so TCP over 443/tcp is needed too. Using 443/tcp gets through pretty much all corporate proxy servers, except the most expensive, govt-level, ones that actually look at the traffic and fingerprint the difference between HTTPS, SSH, and OpenVPN (all use openssl). To most corporate filters, ssl is ssl is ssl.

Any client from outside the protected LAN that you want to have access inside would use the VPN. Yes, that would include wifi users.

There are 50 other ways to accomplish what you want. Each as pros and cons.  With a VPN, you'd have much more capability, so it makes sense (to me) to just set that up.  Having secure access to your home network from anywhere in the world is really nice. The fact that it also works from a slightly different subnet over wifi from your home is just handy too. ;)

---

### Post by zkab on 2018-02-10
OK - if I understand you correctly it should look like this in my case ...

Internet <--> router <--> VPN server <--> switch <--> LAN users & WiFi users

---

### Post by TheFu on 2018-02-10
No.  Wifi should be connected to the router and be on a different subnet from all other users.
VPN can be on the LAN inside the switch or outside the switch. Doesn't matter.

If the router doesn't support multiple LANs, either get a better router or buy another router.  I would assume ipfire can.

---

### Post by zkab on 2018-02-11
OK - thanks

---

### Post by TheFu on 2018-02-11
> **zkab said:**
> OK - thanks

I'll try to make a diagram, if I can get my Visio license to work under WINE.

---

### Post by zkab on 2018-02-17
How is it going with Visio license under WINE ?

---

### Post by TheFu on 2018-02-17
> **zkab said:**
> How is it going with Visio license under WINE ?

So ... found that libreoffice can read visio files and there are templates and stencils full up the same network equipment.  Basically, I stopped trying to get visio working.  Played with libreoffice for 10 min then , like  a dog following a smell, got side tracked by a squirrel (rocket stove build) and headed in that direction. ;)

What was the question?

---

### Post by zkab on 2018-02-17
You mentioned something about making  a diagram of your solution ...

---

### Post by TheFu on 2018-02-17
So, I made a diagram.  
Don't know how to connect it here.  
I'm not a cloudy service user, so providing a link isn't something I can do.

---

### Post by zkab on 2018-02-18
You can send it me with Private Message

---

### Post by TheFu on 2018-02-19
[https://ubuntuforums.org/album.php?albumid=2644](https://ubuntuforums.org/album.php?albumid=2644) ? Does that work?  The file without the icon/image, is the source libreoffice file.

---

### Post by zkab on 2018-02-19
Thanks for the diagram

---

