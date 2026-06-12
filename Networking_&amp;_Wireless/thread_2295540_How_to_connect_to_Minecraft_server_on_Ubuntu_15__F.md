---
title: "How to connect to Minecraft server on Ubuntu 15?  Frustrating..."
date: 2015-09-19
forum: Networking &amp; Wireless
---

### Post by Rick_Astley on 2015-09-19
My son really wants to play Minecraft on the PC and we bought a book titled 'Adventures in Minecraft'. We've been able to get the Bukkit package installed and the Minecraft server running. The package Gufw shows that when the Minecraft server is running (both client and server are on the same physical machine) it uses port 25565. When I go into Multi-Player mode in Minecraft and try to join a server no servers show up when scanning. When I elect to Direct Connect I type in 'localhost' for the IP address and the connecting process times out. I'm pulling out what hair I have left over this Please help.

---

### Post by ArgentWarrior on 2015-09-20
Just run ```
ifconfig
``` and type in your local IP. Always worked for me. 
You might also want to open port 25565 in UFW if you intend to let others join.
```
 sudo ufw allow 25565 
```

---

