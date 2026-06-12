---
title: "Internet Connection Sharing problems through wireless router"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by gyzer on 2008-05-20
I have a bit of an odd setup that I can sometimes get to work, but it defiantly doesn't work all the time, and I'd like to see if I can get some ideas on a better setup without buying any additional equipment from what I currently have.
 
I have two desktop computers, one running XP, and another running Ubuntu 8.04, and I have a laptop, currently running Xubuntu 8.04.
 
My two desktop computers each have D-Link DWA-130 Wireless 802.11N USB network adapter. My laptop has a Atheros(sp?) 802.11g PCMCIA NIC. The house has two wireless networks, an N based network, and a G based network. The house I live in is quite old, the downstairs (which is where the DSL modem is and both the N and G based wireless routers reside) was built in the 1940's and the upstairs, where I reside with my two desktops and laptop is about 10-15 years old. Our wireless can get a bit funky cause of the older construction of the house, one of the reasons we have an N based network on the desktops. 
 
My goal is to get the laptop connected to a network, N or G it doesn't matter I just need something that works. Where the laptop gets used in the house, which is only used upstairs, it gets only a 20%-35% signal from the G network at best, and alot of the time it will drop the signal. So I got the great idea to try to do internet connection sharing through my XP desktop via a netgear wireless router (WGR614 v6). So the connection sharing would look like this:
 
DSL Modem
|
|
Wireless N Router-----Wireless G Router
|
|
(Wireless NIC)
Windows XP Desktop
(Wired NIC) 
| 
|
WGR614 Router
| 
| 
Laptop 
 
I have disabled DHCP in the WGR614 Router, and set the DNS and the gateway on the WGR614 Router to point to the Wireless N Router and set the Wireless N Network adapter on the XP Desktop to internet sharing and it has worked, for at least a time. I haven' really gotten this to work well for the laptop in Xubuntu, but I was playing with Damn Small Linux before that and it would work for awhile but then drop the signal or the internet connection, I couldn't tell which.
 
I'm having a feeling that the problem I'm having with this setup and Xubuntu has something to do with DHCP and the IP address that's being used on the laptop (192.168.0.X) or some conflict between the laptop and the windows xp desktop's wired NIC that's connecting to the WGR614 Router (wired NIC is 192.168.0.X)
 
So I would like to know if it would be a better idea to do this via my Ubuntu Desktop rather then my windows xp desktop or if there are some settings that I should double check or change, like pointing to the Wireless N Router for the DNS and the gateway? Or is this a problem only with the Xubuntu machine in which I need to configure its IP, DHCP, DNS and Gateway settings differently from the automatic settings that its currently using which does work with the Wireless G network thats downstairs but has a bad signal strength?

---

### Post by SpaceTeddy on 2008-05-20
if you want to do the internet sharing via your Ubuntu desktop - i've written down a [[COLOR="Blue"]guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") for setting up any ubuntu computer as a router.

if you want to stick with the windows xp - i cannot help as i cannot debug the windows side of the problem... sorry. I've been removed from windows for too long :(

if you do use the ubuntu, and the guide does not work for you or your get stuck somewhere- just ask. I'll be trying to answer as understandable as possible :)

hope it helps :)

---

### Post by gyzer on 2008-05-20
Thanks. I think I'm going to continue to try to get it workin in windows a bit longer, then if not I'll try using my ubuntu box.
 
I do have a feeling that if I use the ubuntu box it'll be alot easier to troubleshoot then with my windows machine.
 
Do you have any sugestions on settings I should use on my router, which is now acting like an access point?

---

### Post by gyzer on 2008-05-21
Well I seem to have gotten it to work really well now. I did a few things on the router like turned on RIP, whether or not that makes a difference I don't know.
 
I also printed a template and made a "parabolic antenna booster" which has also helped some. Increased the signal strength by 5-15% and made the connection much more stable.

---

### Post by SpaceTeddy on 2008-05-21
RIP ?  that is hardly likely that did anything... that is an interior gateway protocol for an AS (Autonomous System). Unless you are running lots of routers in your internal network, this protocol is most likely not needed... 

but congratulations on getting your connection to work better :)

---

### Post by gyzer on 2008-05-21
Yeah I know that isn't probably what did it, but it definatly isn't hurting anything.

---

