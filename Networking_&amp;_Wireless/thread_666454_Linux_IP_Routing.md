---
title: "Linux IP Routing"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by absolutesantaja on 2008-01-13
Hi, I'm working on a project for my counties local school system. We are building linux firewalls to be placed at the different schools and i'm trying to figure out how to set them up. We currently have two different sets of IP addresses one public one private and they are divided into subnets at each school. Currently we can access any computer at any school as long as we are inside the private network and i would like to maintain this ability when i setup our firewalls but still be able to do port blocking between subnets. Each computer being built for the firewall has two network cards, one will be tied into the local isdn gateway/router at each school and the other will go into our 128 port switch. If anyone knows where  I can find information on setting something like this up please let me know. I have already read several posts and have been searching throughout this forum.

Thanks
Shawn Weeks
[email]absoluteXXXXXsantaja@gXXXmail.com[/email]
(remove the x's)

---

### Post by HermanAB on 2008-01-13
Well, how do you mean 'access'?  

For admin purposes, use SSH and limit logins in /etcsh/sshd_config to the IP addresses of the schools.

Cheers,

Herman

---

### Post by absolutesantaja on 2008-02-19
right now you can access any computer in the county from anywhere else even though they are on different subnets. I'm guessing the routing tables in each router take care of all the footwork. For the most part I've come to the conclusion that we can't do it since we can't change the routing tables on each schools router. The state owns them and doesn't let us do anything. We're gonna end up doing something else since there isn't a way to retain this unrestricted access between schools without doing vpn.

Thanks

---

### Post by The Cog on 2008-02-20
The state owned routers will be configured as the default gateway in all your PCs. You could reconfigure those PCs to use your firewall as the default gateway, and have the firewall route packets for other schools to the state routers and other destinations out to the internet. 

You will need to know the addresses of all the other schools and the IP address of the address of the local state router to forward inter-school packets to in each case.

There may be political jurisdiction issues with the state schools board to consider too, but that's your call.

A good reference might be [http://linux-ip.net/html/routing-intro.html](http://linux-ip.net/html/routing-intro.html) .

---

