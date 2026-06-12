---
title: "Setting up a simple LAN (with internet by way of cell phone tether)"
date: 2014-08-16
forum: Networking &amp; Wireless
---

### Post by domtron on 2014-08-16
Hi, I'm trying to set up a two computer LAN. I am fairly good with the terminal, but know little about networking. I've done some reading but haven't made much progress.

I have two computers one ubuntu(13.04) and one lubuntu(12.04). The ubuntu computer has the internet connection by way of cell phone tether(android, easytether) which I need shared with the other computer. This seems to complicate things since the internet stops working on the ubuntu computer when I connect an ethernet cable between it and the hub. The cellphone tether uses a virtual network adapter called easytether0. I manually set each computer with ifconfig eth0 192.182.1.x netmask 255.255.255.0 where on the ubuntu machine x=0 and on the lubuntu one x = 1 (also tried x= 1 and 2 respectively). I would like to assign IP adresses automatically, if possible, so I can just add and remove devices.
_&#8203;_
My hub is and old 8 port 10baseT which I got third+ hand for free ([http://www.milan.com/TransitionNetworks/Uploads/Downloads/Obsolete/7334_ETBTHB0801.pdf](http://www.milan.com/TransitionNetworks/Uploads/Downloads/Obsolete/7334_ETBTHB0801.pdf)). The hub lights up when powered and when the computers are plugged in. When I set up both machines to try and ping each other the red network activity light blinks.

Does it sound like the hub is bad or am I just doing something wrong. I can get a better hub later but I'm a bit short on cash atm. I read somewhere that just because ping says the other host is unreachable doesn't mean there is no hardware connection to it(something about the other host not knowing how or where to respond). If so how do I test the connection/fix the software problem.

Keep in mind I would like to eventually add a shared printer, a NAS, and a few more computers.

Thank you for any help you can provide. It is very appreciated!

---

### Post by TheFu on 2014-08-17
You need something to be a "router" - a hub is NOT a router.  That means one of the computers must handle the routing.

---

