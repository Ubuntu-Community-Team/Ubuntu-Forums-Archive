---
title: "Macbook doesn't work with Static IP"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by MacMouse on 2008-04-30
Hi,
I have a home network, Belkin router in the middle, and a few Macintosh OS X computers already receiving internet access off the network.

One of the Macbooks is running Ubuntu, and it can receive the internet only if it is set to DCHP (dynamic IP). If I switch the Macbook (and the Belkin router) to Static IP it cannot receive the internet, either wired or wireless.

I've opened the Ubuntu network panel, and re-entered the network settings a hundred times, but it still doesn't work.

IP address = 192.168.2.4
Gateway address = 192.168.2.1
Subnet Mask = 255.255.255.0
DNS = 203.0.178.191 (that's [iiNet]("http://www.iinet.net.au/support/broadband/settings/") Australia)

I wonder if there is something else that must be done before I can connect with a static IP address. All the other computers (Macintoshes) on the network are accessing the internet fine on the same settings.

Any ideas?
thanks

---

### Post by superprash2003 on 2008-04-30
i think its got to do with the way you have configured your DNS servers.. read this - [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) .Opendns servers are used above but you can change them with whatever DNS servers you like..although opendns is recommended

---

### Post by MacMouse on 2008-05-03
Thanks for your reply, superprash2003. I changed to the open DNS servers you suggested, but it didn't solve my problem.

I can't even access the router address 192.168.2.1 when in static IP mode. I wonder what else it could be? Where else should I look?

---

