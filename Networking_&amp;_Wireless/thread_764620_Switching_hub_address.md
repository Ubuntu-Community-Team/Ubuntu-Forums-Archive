---
title: "Switching hub address"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by PouncingAnt on 2008-04-24
I have a 5 port buffalo switching Hub (LSW-TX series), bought in Japan, and need to access it with my browser to edit the settings, but unfortunately I've lost the IP address, and no amount of searching the internet has found me a solution yet.

is there a command which will get me the hub's IP address? ifconfig just gives me the IP of the router.

My PC  ->  Hub  ->  Router(dhcp server)

I want to limit or otherwise block P2P on my network, but the router has nothing useful for that. Was hoping the hub would be better..

---

### Post by netztier on 2008-04-24
> **PouncingAnt said:**
> I have a 5 port buffalo switching Hub (LSW-TX series)
...
Is there a command which will get me the hub's IP address? ifconfig just gives me the IP of the router.

Hubs and unmanaged switches generally don't have IP addresses. Only "managed switches" or "managed hubs" (although these have become *very* rare these days) have an IP address and a telnet, ssh or web interface. 

I'd be surprised if a simple 5-port switch was of the "managed" kind. And if it was, it should have some "reset" switch you can press to bring it back to factory default settings. In that case, the manual should tell you what the original IP address is.


> **PouncingAnt said:**
> I want to limit or otherwise block P2P on my network, but the router has nothing useful for that. Was hoping the hub would be better..

That's not a function of a hub or switch. Hubs are simple signal repeaters. Switches only know about MAC addresses and are completely blind to the IP and TCP/UDP information in the packets they forward.

This has to be done on the router - a Router knows about IP addresses, and some of them can inspect TCP/UDP information in the packets and throttle, block or prefer some services to others if needed.

regards

Marc

---

### Post by PouncingAnt on 2008-04-24
Odd, I thought I'd managed to find it's page at some point. Must have been something else I guess.

The router doesn't seem to have any way of blocking ports, but thats something I'll have to address in a different forum, I spose.

---

