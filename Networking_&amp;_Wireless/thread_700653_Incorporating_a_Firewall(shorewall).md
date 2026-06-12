---
title: "Incorporating a Firewall(shorewall)"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by TechMansoor on 2008-02-18
Currently I have a couple of workstations and a ubuntu server acting as a mediatomb server and soon to be backuppc box. I have a basic netopia 3000 isp given modem/router. I have recently installed shorewall on that same ubuntu server and I want everything of course to go through it for protection.

My question is, how can I make all access hit the ubuntu server box? I know I need to make it the gateway, but I have my netopia device acting as the modem/gateway, and the router as well.

What do you guys think I need to do?

---

### Post by bwhite82 on 2008-02-18
You need to turn off DHCP on the router, make your new firewall do that (it should have this capability). If not, check out SmoothWall. Anyways, set your workstations, and anything else you want to go through the firewall to the gateway address (that you set) of your firewall box. That takes care of the green (secure) side of things. Now you have to set the red (external) gateway in your firewall to the IP of your modem. I hope all of this made sense to you. It helps to map out a diagram.

-Cheers

---

### Post by TechMansoor on 2008-02-18
> **Soldierboy said:**
> You need to turn off DHCP on the router, make your new firewall do that (it should have this capability). If not, check out SmoothWall. Anyways, set your workstations, and anything else you want to go through the firewall to the gateway address (that you set) of your firewall box. That takes care of the green (secure) side of things. Now you have to set the red (external) gateway in your firewall to the IP of your modem. I hope all of this made sense to you. It helps to map out a diagram.

-Cheers

I knew thats what I had to do indeed. Thanks a billion soldierboy..

One question though..

Set the red external gateway in my firewall??

---

### Post by bwhite82 on 2008-02-19
Yes. I assume the first device in the "chain" is your modem, correct? Hence that is the primary gateway. Your firewall needs this information. I've never used shorewall, so it may determine this automatically. In smoothwall I had to set it, in my case my modem's gateway is 192.168.0.1.

---

