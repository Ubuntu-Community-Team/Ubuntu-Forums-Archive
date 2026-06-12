---
title: "Connecting a game server"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by william_hunter on 2007-02-27
OK, I am having a problem with a new system I built for the express purpose of hosting a NWN gameworld. First, let me say this. I know I need to open ports in my hardware firewall to post the game to internet. I have had a windows machine running the server for more than a year now, so I know what ports need to be open. For some reason, I can't make the Linux box visible to the players. I can see it behind my LAN as long as I let the router assign the IP via DHCP. 

Does Ubuntu come with a firewall?

---

### Post by william_hunter on 2007-03-04
OK, so I seem to have figured out some of this. Seems there are a number of ports that needed to be opened. So, I set my router up to set the Linux box as DMZ, then opened the required ports on the box itself. I think the problem lies in the fact that linux doesn't broadcast itself to the internet, but it seems to be working now.

---

