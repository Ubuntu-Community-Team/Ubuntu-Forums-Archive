---
title: "Will this setup work?"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by cic007 on 2007-04-22
Hey guys,

Advice would be very welcome on the network setup diagram attached. I intend to attempt it as soon as my second wireless router arrives.

Will it work?

Can anyone forsee any difficulties? Or fancy features I'll need to play with in the setup?

I would have ideally liked to use Ubuntu on the connection sharing computer but that was proving very problematic and I've given in. Anyway it's currently working well for ICS under a similar arrangement (except it just goes to the Xbox instead of a router).

Help and advice requested! 

Is there some clever setup I'll need on the router?

or will it all just work?

Thanks again for everything folks.

Long live ubuntu!

---

### Post by chili555 on 2007-04-22
I am no expert on these things, my only qualification is I have a very similar setup running now. I set it up mostly with trial and error and guesswork.

The key is WDS and here is a tutorial:  [http://www.dd-wrt.com/wiki/index.php/WDS_Linked_router_network](http://www.dd-wrt.com/wiki/index.php/WDS_Linked_router_network)

I have my network on the same ESSID. All wireless devices get an IP address via DHCP, all wired statically. Router #1 is 192.168.1.1, which is set to serve DHCP, and router #2 is 192.168.1.2, which has DHCP turned off. All devices see each other via fping, ssh, rsync and, although I never tried, I'm certain, FTP.

I had to flash the most recent firmware on router #2 to get WDS.

---

