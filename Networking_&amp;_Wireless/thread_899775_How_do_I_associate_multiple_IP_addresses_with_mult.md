---
title: "How do I associate multiple IP addresses with multiple Xen instances on Ubuntu 8.04?"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by tominglis on 2008-08-24
Dear All,

I've received multiple IP addresses from my ISP, and I want to get them working with multiple Xen instances on my Xubuntu 8.04 server, but I am not sure how best to proceed.

I have been given a network address, 13 useable addresses, a router address, a broadcast address, and a subnetmask.

At the moment I have a Belkin Wireless G ADSL Modem / Router on my ADSL internet connection.

My server has two Gigabit ethernet adapters built into its motherboard, and one of these is connected to the router. It has a local IP (through the NAT) of 192.168.7.200. I have 8 Xen instances on the server, all with similar IP addresses, i.e. 201, 202... 208.

The router receives it's IP address, subnet mask, and gateway automatically at the moment over PPPoA, but I can specify these manually if I want to.

I can also associate the router's IP address with one other device through DMZ.

Will I need to buy a new router of some kind to be able to recognise the 
additional IP addresses and route them onto the individual server instances? (If so could you recommend one?)

Or can I somehow use the one exposed IP address pointing to the server (through DMZ) to virtually assign the additional IP addresses to the individual server instances?

Any help would be hugely appreciated!

Many thanks,

Tom

---

### Post by bab1 on 2008-08-24
All the virtual NIC's need to be briged to the physical NIC.  Here is a [[COLOR="Red"]**link**[/COLOR]]("http://www.google.com/search?q=lifehacker+virtualbox&btnG=Go%21") to an article using bridging.  It uses VirtualBox, but you will get the idea.

---

### Post by tominglis on 2008-12-22
I am not sure which article this is supposed to be linked to?

I think another way that I could do this is to keep the local NAT IP addresses I currently have for the Xen instances, but to buy a router which allows me to map each of my static IP addresses to the local addresses (i.e. a router that does routed IP and NAT at the same time). Does anyone know of such a router?

---

