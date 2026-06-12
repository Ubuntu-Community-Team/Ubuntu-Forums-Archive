---
title: "Any way to get a web browser to listen to a specific network interface?"
date: 2015-09-30
forum: Networking &amp; Wireless
---

### Post by vperaino on 2015-09-30
So if I have a computer with two ethernet interfaces (eth0 and eth1), and one is plugged into our normal LAN/internet network here in the office while another is plugged into our VoIP system (which is physically separate, save for congregating in the same ethernet switch on different subnets/VLANs), is there any way I could perchance make it so that Firefox listens to the internet traffic and Chromium listens to the VoIP traffic? The network options are fairly limited in scope inside the browsers themselves, I realize. 

The reason is that it'd be much easier to just use separate browsers to access the different network equipment for each system (SIP phones vs. laptops, etc.).

The internet/computer network is on 192.168.2.x and the VoIP network is on 192.168.3.x

---

### Post by TheFu on 2015-09-30
It is a routing question.  Plus VoIP is usually SIP and connects to a local SIP server - no routing to the internet is possible. Does Chrome have a built-in SIP client?

---

### Post by vperaino on 2015-10-01
There is a local Trixbox server. The server has three connections - one going into our general LAN (for web GUI access), one going into the subnetted phone network, and one going out to a T1 connection which is how our phone system operates (don't ask, it was like that when I got here). 

Being able to plug into the phone network would make it simpler for me to adjust settings on the SIP phones themselves, which can't be accessed from the regular network (unless there's some mystical networking woo that I'm not aware of).

---

