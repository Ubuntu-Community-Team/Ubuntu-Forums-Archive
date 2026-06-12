---
title: "How to Route Requests By Hostname"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by dcurran on 2007-06-26
I have four ubuntu machines sitting behind a linksys router, one is running Feisty Fawn and three are running Edgy.

The router has a single static IP address and the local address of 192.168.1.1, the four machines are 192.168.1.100, 192.168.1.130, 192.168.1.131, 192.168.1.132

I would like to setup the Feisty Fawn system to have all incoming requests on all ports routed to it, and the have this machine handle re-routing the requests to the Edgy machines based on hostname.

This way I can have four different DNS names be handled by the different computers.

site1.org -> 192.168.1.100
site2.org -> 192.168.1.130
site3.org -> 192.168.1.131
site4.org -> 192.168.1.132

I would like to have SSH, SFTP, POP, SMTP and HTTP enabled on all of these machines.

I have done a good deal of looking for something that would allow this to happen, but I have not found anything that describes how this would be accomplished.

Does anyone know how I could do this?

---

