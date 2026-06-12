---
title: "How to create a VPN connection in Ubuntu?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by HQLCD on 2008-08-10
How to create a VPN connection (connect to server, etc.) in Ubuntu and how to make it auto connect upon when the users logs in to the system?

---

### Post by gseeli on 2008-08-10
I would recommend looking into VPN Connection Manager in the Add/Remove Applications and see what you can do with it. It incorporates with the Network Manager, so there might be a way to auto-connect but I haven't looked into it.

Hope that helps a little,
Gseeli

---

### Post by SpaceTeddy on 2008-08-11
mhm - this question is about the same as "how do i drive to rome"... I don't even know what you are trying to accomplish.

But here is my guess what you might want:
You want a server that runs some sort of vpn-server. This server then sits somwhere in the internet and waits for clients to connect. 
The clients are run automaticially on the computers of the users. As soon as they turn them on, they will automaticially connect to the server, thus giving the clients access to some network or at least the server itself whereever on the globe they are. As soon as they are connected, they can access the server.

If this is what you want - i would suggest openvpn. 
You will need the following requirements to do this :
 - A Hostname of the server that does not change or a static ip
 - Accessibility to this server on any port (standard for openvpn is UDP 1194)
 - An internet connection that can handle the traffic from the clients
 - A good idea what you want the client to access

Everything else is a software problem and can be handled quite simple. 
Also - i must confess that i am a huge fan of OpenVPN. there are other VPN-servers out there that might work as well - i only use OpenVPN tho.

hope it helps :)

---

### Post by Iowan on 2008-08-11
Anything [here]("https://help.ubuntu.com/community/SSH_VPN") help?

---

