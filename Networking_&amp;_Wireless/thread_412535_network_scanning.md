---
title: "network scanning"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by eier on 2007-04-18
i have a problem, i live in a dorm and the doem router has only port 80 open,
and som smart guy is using peer to peer program trough the 80 port, so no one else can use the internet,cant even access google.
anyone know of a program to find he's ip?I'm using ubuntu 7.04:confused:

---

### Post by tturrisi on 2007-04-18
You can use any network sniffer to sniff the traffic & see who's doing what, along w/ the ip addresses and ports/protocols used.  However, if the router has a switch, you will only be able to sniff your own traffic.  To see all traffic you'd need to place a hub between the router & other computers, then plug your comp into the hub & sniff away.  This is because a switch sends data ONLY to the destined mac address connected to it whereas a hub sends to all mac addresses connected to it.  Switches are "smart", hubs are "stupid".

---

