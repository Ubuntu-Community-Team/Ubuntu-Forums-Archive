---
title: "Resolving local hostnames"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by geecko on 2006-10-21
What programs do I need to install/configuration do I need to do in order to be able to ping, rdesktop, and access http for other computers on my local network only specifying the computer's name. For example, I'd like to be able to "krdc rdp:/homeuser@galactica" instead of "krdc rdp:/homeuser@192.168.1.101". 
Is this configuration any different if I'm trying to connect to a Windows Server 2003 or Windows XP or Ubuntu box?
My network is using a Linksys router as the DHCP server; should I be relying on it to resolve my local network hostnames?
(Also if there's a solution that has a KDE frontend, I'd probly prefer that)

Thanks in advance :)

---

### Post by kidders on 2006-10-21
Hi there,

A DHCP server isn't responsible for name resolution, but it *is* responsible for telling network clients *how* to resolve things.

You have two basic options, imo ...

**1 - The hacky way**
Add entries for all your computers to every computer's /etc/hosts (or equivalent), and be prepared to constantly modify them all, in the event anything changes.

**2 - The "smart" way**
Install a DNS server on one of your boxes, and consider replacing your router's DHCP server with one of your own too. If you did both, not only would all your DNS information be in one place, but you'd have better control over how your network was configured.

I hope that helps.

---

### Post by geecko on 2006-10-22
Okay, so it seems like I shouldn't be counting on the router to provide DNS-like services.

A DNS server sounds like it might be good, but I think I'd like a more ad-hoc solution that just runs on the Linux machines that need it (the Windows machines are somehow resolve hostnames without any extra setup).

Back in Dapper, I remember seeing a service called Lisa, which I guess has replaced now be Zeroconf and Avahi.

Is Zeroconf/Avahi maybe what I'm looking for? Should it work right out of the box?

---

### Post by spd106 on 2006-10-23
Windows use netbios broadcasts to resolve hostnames. Samba and winbind can be used to integrate with windows hosts. There are many other threads with howtos on this topic already. Alternatively, you can have a DNS server, but will need to be available for all PCs ie 24/7. Sadly this isn't incorporated into most home/consumer routers by default, they just handle dhcp.

Avahi/Zeroconf will work as well, but you need to do some fiddling as you will need a zeroconf client for the windows PCs. Apple have a free to download client.

---

