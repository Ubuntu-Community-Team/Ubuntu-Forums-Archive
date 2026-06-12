---
title: "Trendnet Router not allowing SSH connecitivy"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by jeepfreak2002 on 2007-05-04
On the recommendation of a user on this forum I am using Trendnet routers for my business.

We are establishing VPN tunnels across multiple locations, and my software folks need to connect through SSH on port 22 to a pc on my LAN. I have forwarded port 22 to the computer that needs to establish the SSH connection.

My software vendor is able to remotely access the router and tweak settings. It appears, by reading the logs, that the attempt to remotely establish the SSH connection hits the router, and then I get an "icmp destination unreachable" message.

I interpret that as meaning the local LAN PC is not listening for the incoming connection, and it is being forwarded correctly. My vendor feels that the router is not directing the connection correctly. They are sending me a router that has been preconfigured, but in the mean time, my OCD nature refuses to believe that my otherwise functional equipment is the problem. Other ports forward just fine.

Anyone have experience w/ Trendnet routers and SSH connections?

Thanks,
Jeepfreak

---

