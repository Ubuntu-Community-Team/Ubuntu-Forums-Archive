---
title: "Mtu"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by SpaceTeddy on 2008-04-05
Hi Folks, 

i've been running into some strange things lately. For the past three days, my ubuntu router (ubuntu 7.10 server, 4 nics) refuses to forward pakets on any device that are bigger than the smallest mtu setup on the  devices that are involved. 

All network cards (eth0 through eth3) are set to a MTU of 1500
Also i have a adsl uplink with a forced MTU of 1492 (attached to eth3). 

The router itself can do anything on any network card, upload, download... no paket loss, nothing. 

Also, any computer in my internal network can download via the ppp0 link. So any paket from the internet can flow through the router to the client without any problem.
However, an upload from a client to the internet (i.e. forceing pakets to have maximum size) will result in the pakets... disappearing. Using wireshark, i can see the paket leave my computer, but running tcpdump on the server show that they do not get there. they just vanish. Mind you, that only happens for pakets which are bigger than 1492 bytes. As soon as i force my computer to drop it's MTU to 1492, all pakets can pass.

I have never seen this behavior before (and i've setup a lot of router over the years). Also, i cannot go about and change the MTU of any device that might connect to my network. So, does anybody have any idea on what the cause of this phenomenon is and how i can fix this to use the normal MTU of 1500 on my network cards.

btw. all three network cards not used for dsl (eth0, eth1, eth2) have the same problem... no matter if i connect directly, have a switch of an access point inbetween. the paket always leaves my computer... and does not reach the network interface of the router if it is larger than 1492 bytes!

thanks for your time and help

---

