---
title: "Configuring NAT"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by hk_2999 on 2006-09-18
This post might be more hardware and internal embedded software type than related to ubuntu.

I had downloaded Azureus for ubuntu, and I saw that in order for it to operate fully, I need to enable NAT on my wireless Canopy internet receiver. How can I set up NAT on my machine?

I have no routers, no firewalls or anything set up.

And I had seen an Enable NAT feature on my Canopy's settings page, but I can't seem to enable Static IP adressing, so I need to know how to do that too.

And there are no Port Forwarding option available in the settings page, but there is an option for Port Mapping. Are they the same? What is the IP I should put on the Port Mapping box. The ports I should open?

---

### Post by timmeeej on 2006-09-18
NAT == Portmapping
I'm not sure what ports Azureas needs, but i'm sure you can google it. 

You can enable static ip adressing by changing your network settings on you ubuntu box. (not on the router). Just fill in all the network settings like ip, subnetmask and gateway.

---

### Post by hk_2999 on 2006-09-18
Ok, im kind of getting the idea.

I've already googled what I should put on those ports to open, and it should be a range of somewhere between 53000 up, since some ISPs(w/c includes mine) blocks those 8000 below to limit filesharing.

But still have one question in mind. What IP shall I put on the Port Mapping IP option, right next to the port to open box: ip, subnetmask or gateway?

---

