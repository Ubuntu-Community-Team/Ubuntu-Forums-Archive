---
title: "Destination Host Unreachable - local ip address"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by sadman64 on 2008-11-07
I am trying to set up an ubuntu (8.10) machine as a local ftp server. it has a static ip address, and i forwarded the port i am using to that address. i am not able to connect to it using it's local address, and when i ping that address i get the message 'Destination Host Unreachable'. however, if i use my external ip address, i have no problem connecting to the server. it is obviously faster to route the traffic internally only, does anyone have any ideas on how to fix the problem?

---

### Post by kerpow on 2008-11-07
Honestly it could be so many things. Are you trying to get to it locally via wi-five per chance?  Can you ping the server locally from another machine?

---

### Post by sadman64 on 2008-11-08
i am using a linksys wrt64g

right now, i am able to ping the gateway from the server, but i am not able to ping any other machine.

from this computer (ubuntu 8.10) i can't ping the gateway or the server

from another computer on the network (windows xp), i am able to ping the gateway but not the server

only the server is using a wired connection, the other computers are using wireless

this is so annoying... i think i'm gonna try rebooting the router

---

### Post by sadman64 on 2008-11-08
resetting the router didn't help

a vista computer was able to ping the gateway and the server, but only able to login with the external ip address

---

