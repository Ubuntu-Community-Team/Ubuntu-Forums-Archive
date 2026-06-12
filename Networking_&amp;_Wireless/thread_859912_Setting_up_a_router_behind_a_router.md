---
title: "Setting up a router behind a router?"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by dracule on 2008-07-15
I have 2 routers.

Right now, Router 1 (now going to be called R1) is connected to a modem

Router 2 (R2) is sitting in my closet.

I have a hacked La Fonera (w/ dd-wrt) router acting as a bridge, currently connected to my xbox 360 via ethernet.

I want to share that connection w/ 2 computers sitting next to my 360, so i want to use R2 to do it.

Is it possible to just plug in the ethernet coming from my bridge to the place where the modem ethernet would normally go?

Is this even possible?

I have searched, but couldnt find any w/ my kind of situation (with a bridge)

---

### Post by superprash2003 on 2008-07-15
yea it should work.. but make sure that dhcp is enabled on the main router.. and the other routers have dhcp off.. this would make the other routers like wireless hubs..

---

### Post by kevdog on 2008-07-15
Also, unless you make a change with ddwrt - make sure that the wire coming from the main router gets plugged into one of the LAN ports (1-4), and not the single WAN port.  This will make your second router like a hub (The WAN/LAN conversion can be changed within dd-wrt to gain one extra port -- however its not absolutely necessary).  (I have this set up with 3 routers connected serially, so I can vouch that it works).  I would also set the first router in the chain to act as the dhcp server and set it to start assigning addresses with something like 192.168.1.100.  I would set the 2 additional routers in your chain with static IP addresses like 192.168.1.2 and 192.168.1.3.  This way there will be no static IP/dynamic IP (via dhcp) conflict.  Other than that, its very simple to do.

---

