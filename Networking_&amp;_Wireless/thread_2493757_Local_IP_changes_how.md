---
title: "Local IP changes how?"
date: 2023-12-23
forum: Networking &amp; Wireless
---

### Post by whiskey76 on 2023-12-23
I have 2 machines connected to ethernet, my main rig and an older machine that runs 3 game servers. The local IP on the game server changed by itself today, so I got a "No route to host" error when trying to ssh from the main rig to the server. And the game servers weren't showing up in-game. 

I went into my router and saw that the server's IP changed from 192.168.1.14 to 192.168.1.20. So I changed the local IP that the ports forwarded to, and this fixed the issue. The game servers are now showing up in-game.

How do I find out why the local IP changed, was it just DHCP (the router uses DHCP)? And what can I do to prevent this? I didn't see an option in the router for IP Reservation. FWIW the router is a Netgear R6700AX, and the game server is Ubuntu Cinnamon 23.10. Thanks!

EDIT: I found the IP Reservation section in Advanced > Setup > LAN Setup

---

