---
title: "How to properly setup a machine from changing private IP address?"
date: 2021-01-17
forum: Networking &amp; Wireless
---

### Post by john561 on 2021-01-17
Greetings,

So I setup a home server, using Ubuntu 20.04 LTS Desktop, to have my files hosted there (synced using NextCloud btw). I have access to them from my Windows 10 PC, but I noticed that at times, the private IP changes for the Ubuntu machine. I make emphasis on private because that's what the network details give me, not the public IP one. I have DynDNS services that point to a hostname and my router (ARRIS) has the option of using Dynamic DNS (Which I have configured). However anytime the Ubuntu machine has it's IP changed, I have to go into ARRIS panel and change the port forwarding IP address (it only accepts private IP and not public IP).

My ISP only offers static ip options but only if I have a commercial account...which I don't have since it's at Home. 

Is there any way to remediate this that doesn't require me to open a commercial account in order to get the static IP? 

Thank you!

---

### Post by TheFu on 2021-01-18
[https://ubuntu.com/server/docs](https://ubuntu.com/server/docs) has a section on networking. In there is how-to setup a static IP for ubuntu Server.

---

### Post by chili555 on 2021-01-18
> My ISP only offers static ip options ***for public IP addresses*** but only if I have a commercial account...which I don't have since it's at Home.

Aren’t you asking about private IP addresses? 192.168.x.y, etc.?

If so, as I assume, It is easy to set a static IP address in the Network Manager interface, just like this: 

[IMG]https://i.postimg.cc/6qX6PjJQ/Screenshot-from-2021-01-18-16-03-26.png[/IMG]

Just be certain to select an address outside of the DHCP pool in the router. If the routers pool is, for example, 192.168.1.2 to 192.168.1.51, then an address of 192.168.1.101 is therefore available.

---

