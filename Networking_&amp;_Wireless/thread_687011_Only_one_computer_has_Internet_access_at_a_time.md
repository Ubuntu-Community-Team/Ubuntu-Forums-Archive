---
title: "Only one computer has Internet access at a time"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by smd0665 on 2008-02-03
Hi. I have a home network setup and recently upgraded my cable modem. Now, I can only get the Internet on one computer at a time. I have to unplug the modem and restart it in order to use the other computer. But, I can no longer access the Internet on both computers on the network at the same time. One computer is running Windoze XP; my main computer is running Kubuntu Gutsy.
Does anyone have any suggestions? I've tried everything. Please let me know if you need further info.

---

### Post by curtlee2002 on 2008-02-04
The internet connection from the modem must me routed to the other computers. If you are using a router plug the modem into the WAN or Interne port on the router. If not I can help you setup Ubuntu to route the connection for the windows computer.

---

### Post by netztier on 2008-02-04
> **smd0665 said:**
> 
Does anyone have any suggestions? I've tried everything. Please let me know if you need further info.

Cable? The cable internet provider here assigns limited amounts of IP addresses for the different subscriptions. The basic subscriptions only get one IP address, the larger ones up to four.

IP addresses are assigned based on MAC addresses - and these are unique to each NIC. The cable modem/cable network remembers which MAC address has obtained an IP address via DHCP - and refuses to dole out another one to a PC connected to the same cable modem if the maximum number for the current subscription is exceeded.

Solution: geht a broadband router with an Ethernet WAN interface, and an integrated 4-port switch (and if you like, one with an integraded WiFi Access Point, often called "Wireless Router"). 

Connect the WAN port to the cable modem - and it will only ever see the WAN port's MAC address and happily believe that it's the single computer using the Internet.  The router will obtain a single IP address via DHCP. To your internal network, the router will be a DHCP server and dole out addresses to your computers.

Their connections will be "hidden" behind the single public IP address - and everyone's happy :-)

regards

Marc

---

### Post by curtlee2002 on 2008-02-04
Thank you netztier for over wording what I said and not giving him the option of using his ubuntu computer as a router. You basically said he must buy more stuff, which is not true, but easier.

---

### Post by netztier on 2008-02-04
> **curtlee2002 said:**
> Thank you netztier for over wording what I said and not giving him the option of using his ubuntu computer as a router. You basically said he must buy more stuff, which is not true, but easier.

Agreed - the OP could use basically any PC with two NICs and activate "Internet Connection Sharing" on it - or whatever the feature is called on the Operating System platform of choice.

It would certainly work, yes, and of course it will with Ubuntu.

But in that case, other PCs could only access the Internet if the "internet sharing" PC is running. I prefer to avoid such dependencies - and the electricity bill price tag they drag along. Keeping a small router running on a handful of watts for 24hrs a day is a different story from running a ~100 watt PC for 17hrs a day to keep the whole family online from 6am to 23pm.

Therefore I generally suggest using small hardware routers for that. Their web configuration interface is often easier to use and therefore may lead to success more easily, as you said. Of course, it's a lot more instructive to learn to do it the Linux/Ubuntu way - for which there is always the Linksys WRT54GL - the wireless broadband router running Linux.

Didn't mean to trod on your feet, sorry.

regards

Marc

---

### Post by smd0665 on 2008-02-07
Hi. Thanks for replying. I am using a router (Linksys EZXS55W). The setup worked fine until I upgraded the modem, though I have moved the cables around to see if it makes a difference. The cable modem is plugged into the uplink port. I've even tried using a specific IP address on the Windoze computer (instead of letting the computer pick one) - when I did that, Network Settings said I was connected, but I still couldn't access the Internet.

---

### Post by netztier on 2008-02-07
> **smd0665 said:**
> Hi. Thanks for replying. I am using a router (Linksys EZXS55W). 

That device is not a router, it's a plain simple 5-port LAN switch. See Linksys' [Web page about this device]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416836711&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3671145678B35"). 


regards

Marc

---

