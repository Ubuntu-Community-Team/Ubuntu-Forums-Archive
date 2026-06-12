---
title: "Small Network DNS/DHCP with Ubuntu Server"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by lurch89 on 2008-06-14
I have a small home network set up with DD-WRT on a WRT54g, as well as an Ubuntu Server (8.04). Everything is working properly, but I want to set up some advanced network.

I want to have an internal domain name "homedomain", so that dns names would be like client.homedomain . I want this hopefully served by the dhcp server on the DD-WRT or else by the Ubuntu server. 

What is the easiest way to do this? Or any good guides on how to do this?

---

### Post by TheLocalGraveDigger on 2008-06-16
this would have to be done from your ubuntu box.download and install bind9 i think to start you off.do you have a high speed modem your router plugs into?

---

### Post by lurch89 on 2008-06-16
I put bind9 on the Ubuntu server, but haven't told the router to advertise it yet. I'm mostly confused with the configuration. And yes, I do have a high-speed connection (cable). Modem goes to router, router goes to network, server is on network. The server does not act as a router.

---

