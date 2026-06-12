---
title: "If the default firewall closes all ports, how come I can still torrent?"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by forsberg on 2007-07-10
Been reading on the threads and found out that the all ports are closed on the default settings of the ubuntu firewall

So why is it I have been able to d/l torrents?  I am using ktorrent with the following ports:

53744 (TCP)
4444 (UDP)
4445 (DHT)

I forwarded all these ports on my router, but havent done anything to the firewall (I wasnt even aware ubuntu had one on by default until today)...

any ideas?

---

### Post by Mr. C. on 2007-07-10
Too little description to know exactly what your setup is, but let's assume the standard setup.

In a nutshell, internally initiated network connections are automatically allowed inbound communications that are associated with the outbound connection.  The torrent protocols negotiate such that your machine initiates the connections, thereby bypassing your firewalls inbound (ingress) rules.

MrC

---

### Post by forsberg on 2007-07-10
A little more about my setup:

Laptop: Acer Aspire 3610
Router: Linksys WRT54G
OS: Ubuntu 7.04

Fresh install (since sunday).  Haven't installed firestarter or anything of the sort.  Just Ktorrent for d/ling.

So what you mean is the torrent app automatically allows the ports on the firewall to be open?

---

### Post by Mr. C. on 2007-07-10
You can see your firewall rules with the command line :

iptables --list

If the lists are empty, there is no firewall running (which is to be expected since you didn't install Firestarter).

Regardless, it is not clear to me that you are understanding the differences between port forwarding, port blocking, and ports that are not in use.

P2P applications are written such that if you allow the uploads, the application will create the appropriate connections such that they can bypass a firewall.

MrC

---

### Post by kvonb on 2007-07-10
I believe the default firewall is what they call "stateful", which means that (so I think) ports are closed unless something from the inside (your computer) requests  something to come inward, ie connections to the bittorent client.

---

