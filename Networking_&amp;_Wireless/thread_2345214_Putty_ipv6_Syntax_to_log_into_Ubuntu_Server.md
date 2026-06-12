---
title: "Putty ipv6 Syntax to log into Ubuntu Server"
date: 2016-12-01
forum: Networking &amp; Wireless
---

### Post by chiques on 2016-12-01
My public IP address is something like :

2605:e000:161f:4051:c4e2:d45a:2e5f:f31a

How do I use this into Putty to log in to my Ubuntu server? A straight copy/paste is not working.



I used to have an ipv4 address (8.8.8.8) and copy/paste worked fine.

---

### Post by TheFu on 2016-12-01
[https://serverfault.com/questions/544050/cant-connect-ipv6-linux-server-via-putty](https://serverfault.com/questions/544050/cant-connect-ipv6-linux-server-via-putty) says to use brackets.
[2605:e000:161f:4051:c4e2:d45a:2e5f:f31a] - it goes on to say that only works for local network stuff. I dunno.

Don't know if that works or not. Haven't used putty in years.  The [docs from the author]("https://the.earth.li/~sgtatham/putty/0.67/htmldoc/") doesn't have any mention of IPv6 support.  Elsewhere on the internet, there is mention of IPv6 and settings to toggle support. There is an "auto" setting which claims to do the expected thing. Don't know the connection between these different "putty" versions/docs.

---

### Post by kingneutron on 2016-12-02
--This may help:
[https://en.wikipedia.org/wiki/Comparison_of_SSH_clients](https://en.wikipedia.org/wiki/Comparison_of_SSH_clients)

--Might want to make sure you have the latest version of putty...

--Also, I don't know if you have admin rights to install programs, but you might want to give MobaXterm a try if putty isn't working for you. 
(standard disclaimer, I have nothing to do with the company, just a happy user.)

---

### Post by slickymaster on 2016-12-02
*Thread moved to **Networking & Wireless**.*

---

