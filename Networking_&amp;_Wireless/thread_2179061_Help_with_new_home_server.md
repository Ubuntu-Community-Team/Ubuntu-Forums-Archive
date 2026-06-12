---
title: "Help with new home server"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by chaos_efphect on 2013-10-06
So first all thank you for any help that is offered since I am totally stuck here.

I have a small bookshelf mico pc I was given that only has a single nic and the usb ports are damaged on it so no way to install a second usb nic. I was toying around with the idea of making this in to a home router for my wired network but ran in to a few snags and I come seeking the guidance of the forums. 

My goal was to take my internet modem and plug it in to lan port 1 on a cheap switch I had, then i wanted to plug the bookshelf pc in to lan port 2, then pcs 1 and 2 in to ports 3 and 4. Sounds simple so far i know but this is where it gets fun. I wanted to set up eth0 to act as my RED or wan facing interface, then I wanted to set up a virtual eth0:0 for my green or lan facing interface. On the green/virtual eth0:0 I was hoping to setup a dhcp server/firewall for pc 1 and 2. So is this possible? All the reading/research I have done makes it sound like its possible but I have yet to find a way or an guides for this.

---

### Post by chaos_efphect on 2013-10-06
So I have been doing some more digging and I found this [Site]("http://programster.blogspot.com/2013/01/ubuntu-create-gatwayrouter-pc-with.html") which states it should work. When I attempt to start the dhcp3 server I get the following error in the log file ```
dhcpd: ** Ignoring requests on eth0:0.  If this is not what
dhcpd:    you want, please write a subnet declaration
dhcpd:    in your dhcpd.conf file for the network segment
dhcpd:    to which interface eth0:0 is attached. **
```

(Will update post when I get home, the error is from memory)

---

