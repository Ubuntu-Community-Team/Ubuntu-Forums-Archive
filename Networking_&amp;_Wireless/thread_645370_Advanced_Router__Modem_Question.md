---
title: "Advanced Router / Modem Question"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by notaloafer on 2007-12-20
This question isn't so much related to Ubuntu as the general world of routing and modems (although all of my servers run Ubuntu =)

What I'm doing is upgrading my current lame internet connection to Business-class workplace with 5 static ip addresses. I'm new to the whole multiple IP addresses coming in on one connection and was curious as to what kind of router I would have to buy to be able to point entire IP addresses and all of their ports to a network IP address (there would be no routing at the router/modem level but rather up to the end user with the dedicated server on allowing/disallowing what ports they want via a server firewall) (i.e. IP address 356.23.4.521 and 4 other addresses come in on the same cable line and I need to point 356.23.4.521 to 192.168.1.3 including all ports).

What kind of routing / modem system am I looking into? Is the hardware I'm going to be needing going to be expensive or can I get away with a Linksys WRT54G with upgraded firmware (such as DD-WRT?) . 

Basically I'm starting up a small web hosting business with a few dedicated servers and I need the people with their dedicated server to be able to manage their own firewall without me having to forward any ports. I'm entirely confused on how this all works so please correct me if I'm wrong on how I'm looking at it =P.

Thanks!!
-Eric

---

### Post by jonallport on 2007-12-20
Most routers will handle this setup without problem, I have a static IP range at home and my 3com officeconnect router had no problems, neither did my old zoom X3.  I've jus pulled a Linksys WRGT54GC out of my bits-box and that seem to handle the setup fine if you just set the internal and external IP addresses to be the same.

The ISP will have tagged on of the assigned IP addresses as your router (usually the first in the range) and this is what the router will get from the radius/dhcp server when you connect.  On the router you just need to TURN OFF NAT, set the router's internal IP address to the same as the ISP assigned address and setup the DHCP server to hand out the remaining pool - simple

---

### Post by jonallport on 2007-12-20
I've just re-read the post and....

No, wait I was right the first time, just ignore this!

---

### Post by notaloafer on 2007-12-20
> **jonallport said:**
> Most routers will handle this setup without problem, I have a static IP range at home and my 3com officeconnect router had no problems, neither did my old zoom X3.  I've jus pulled a Linksys WRGT54GC out of my bits-box and that seem to handle the setup fine if you just set the internal and external IP addresses to be the same.

The ISP will have tagged on of the assigned IP addresses as your router (usually the first in the range) and this is what the router will get from the radius/dhcp server when you connect.  On the router you just need to TURN OFF NAT, set the router's internal IP address to the same as the ISP assigned address and setup the DHCP server to hand out the remaining pool - simple

I could see how this would work with 1 static IP address but will it still work if I have 5 static IP addresses that need to be pointed to 5 different servers on the LAN? How would I do that? (I'm not exactly sure how to disable NAT on my WRT54G). I believe Comcast provides a new modem when I upgrade my connection so I'm guessing it will have some kind of administrative interface as well?

-Eric

---

### Post by trobbins on 2007-12-20
Your Comcast/cable modem acts as a bridge between their network and yours.  Think of it as a switch.  Instead of the usual setup where you only get one IP, Comcast sells you 5.  That means that 5 IPs will be allocated to your bridge.  

Plug your cable modem into a switch as well as all PCs that need routable IP addresses from Comcast.  Your modem will give IPs to any devices that request them.  Nothing fancy is involved.  If you wish to have a firewall appliance between the modem and your switch, that's an option, not a requirement now.

The whole reason SOHO routers caught on was because ISPs notoriously only gave one IP per paying subscriber.  Also, NAT by design can offer additional security.

---

