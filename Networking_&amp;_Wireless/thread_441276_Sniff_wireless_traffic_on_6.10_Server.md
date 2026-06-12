---
title: "Sniff wireless traffic on 6.10 Server"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by Tom G on 2007-05-12
Hey

I installed Ubuntu Edgy Server on one of my old PC's (no GUI), and i want to sniff all wireless Tx and Rx traffic (chatlogs, html requests, ...).

I got a Topcom SkyR@CER PCI 154G in it as a wireless NIC.

Now: can someone explain how to capture all the packets (and convert them to a readable format)?

Every computer in this house is connected with wifi, and all running Windows, except for mine. I also can't install any 'loggers' on the windows boxes.

i read something about dsniff, arpspoof,... but i can't get these to work. Or better: I don't understand everything about those

PS: I'm not doing this to invoke some's privacy, i just want to know what exactly goes in and out my router...

---

### Post by tturrisi on 2007-05-12
Your best option would be to run Kismet and lock it to the channel that your ap uses.  Kismet, however, will grab all available wlan traffic from a aps in range using that channel.  Then open the kismet.dump in wireshark to see the captured traffic. To use kismet, your adapter must have a kismet supported chipset.  I never heard of Topcom.  What chipset does it have?  Driver?

Your router probably has built in logging too.  Use that to see what goes in & out.

---

### Post by Tom G on 2007-05-13
The driver i used is mrv8k51.inf, a Marvell Chipset.

And i guess i find a how to on Kismet on google?

---

### Post by tturrisi on 2007-05-13
Marvel chipsets, afaik, only work with ndiswrapper & the windows driver.  This means the device cannot be put into rfmon (monitor) mode and thus will not work w/ kismet.
[http://www.kismetwireless.net/](http://www.kismetwireless.net/)

If you have a router AND a separate AP then you could sniff all the AP  lan traffic by connecting the AP to a hub and then connect the hub to a router port.  The sniffing comp must al;so be connected to the hub.  A switch won't work, has to be a hub.  Then use wireshark to grab all data passing via the hub.

---

