---
title: "Is it possible to WakeOnLan over internet through a hardware router?"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by Crakie on 2007-01-06
This may not be an Ubuntu topic exactly, but since there is some documentation about it around I'll go ahead anyway :)

My AB9 Pro motherboard and onboard LAN controllers support WOL, although I may need to update the bios. I am still reading up on that, but the instructions seem clear. Before updating, I am wondering if it is possible at all to succesfully WOL my computer though. 

The LAN controller is connected to a router. So not a computer, but a little box that resembles a modem. There is only one computer on that router. 

If the computer is turned off, the ethernet LED goes off, but the ADSL LED stays on. This leads me to believe it remains connected, which should mean my IP adres is 'out there' even when my computer is off, right? 

(While writing this, it occurred to me that I can simply ping my IP adres when my computer is off from a remote location to test that) (Also: my IP is static, I think. It does not change everytime I login and my provider sent me a letter stating it). 

If I have an IP adres, I should be able to send a WOL packet to my LAN controller, provided I forward the correct port, right? 

Another thing that puzzles me, is the subnet mask. With WoL utilities, you have to specify it. What are subnet masks, and which one do I need to use?

Thanks,

Crakie

---

### Post by Crakie on 2007-01-07
I know it's not good etiquette, but *bump*

---

### Post by Cynical on 2007-01-07
[quote=Crakie]If the computer is turned off, the ethernet LED goes off, but the ADSL LED stays on. This leads me to believe it remains connected, which should mean my IP adres is 'out there' even when my computer is off, right?[/quote]
Yes. Your router will have the external ip address, and will forward data requested by any computer on your network with an internal ip address. 

[quote=Crakie]Another thing that puzzles me, is the subnet mask. With WoL utilities, you have to specify it. What are subnet masks, and which one do I need to use?[/quote]
A subnet is a group of addresses that belong to you. A subnet mask defines what part of an address is the network part and which is the host part. For more information you can read the wikipedia entry on [subnetworks](http://en.wikipedia.org/wiki/Subnetwork).

But fyi in your case you'd be using 255.255.255.0

[quote=Crakie]If I have an IP adres, I should be able to send a WOL packet to my LAN controller, provided I forward the correct port, right? [/quote]
I don't really see your network topogoly but I'm pretty sure it will. Give it a shot :P

---

### Post by Crakie on 2007-01-08
> **Cynical said:**
> Give it a shot :P

Thanks, I will :D

---

