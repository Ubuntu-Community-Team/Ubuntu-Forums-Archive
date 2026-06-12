---
title: "remote into ubuntu box with dynDNS from windows box"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by pham0167 on 2007-04-04
If I can get some help with this topic, it would be much appreciated!!! I'm also pretty new to linux as well. I have an ubuntu installed on a laptop that is behind a router, it is connected wireless and was getting a dynamic IP.  I would like to be remote into the laptop from a windows box and work on it....I am not creating a webserver or anything, just want to remotely work on it either through a desktop GUI (preferrably) or through a terminal.

What I have done so far:
1. registered with dynDNS
2. configure the Netgear router to update dynDNS
3. changed the ip configuration to be static on the laptop (has access to the internet)
4. configured port forwarding the router to the new static ip address

This is where I'm not sure what to do next
1. I've installed an ssh server, and tried to connect through Putty...Putty was able to see the ip address of router but does not connect ... i get a "Network Error: Connection time out" message ....so I know that dynDNS is working, but not necessarily the port forwarding. 

2. I turned on remote desktop via System > Preference > Remote Desktop
I downloaded both RealVNC and VNCDotNet and tried to connect via the dynDNS host name with luck...i get a "unable to connect to host: Connection refused"

Can anyone shed some light to a newbie? Thanks very much

---

### Post by Snowin on 2007-04-05
This is pretty much the setup that I use to get into my machine from work to use all the bandwidth to download things whilst my wife and I are at work.

Basically, you router doesn't have an SSH server available on it, so it drops the connection.  To get round this is actually quite simple though.

Assign you machine behind the router at home a static IP address in the routers managment interface.

Setup  "port forwarding" to send traffic inbound on port 22 (SSH) to your laptop's static IP address.

That's all I needed to do with mine :)

Good Luck,

Snowin

---

