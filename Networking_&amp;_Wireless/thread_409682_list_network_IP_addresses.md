---
title: "list network IP addresses"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by HereInOz on 2007-04-14
<Resolved>  After a fashion, anyway.  I am running Darkstat, and that is giving me what I need, after I sift through all the Internet traffic.  I was hoping for a static list, but this will do it.

-----------------------------------------------------------------------------------------------------------------------------------------------

 Hi all,

I've been searching for this for a while now, and no doubt posts already exist for it, but I just can't seem to jag the right search criteria.

All I need to know is:

Is there a command that will list all the ip addresses of all the computers and devices connected to my LAN?  

I could probably do this with a packet sniffer, and watch where everything goes, but is there an easier way?

Hope you can help.

---

### Post by PilotJLR on 2007-04-14
There is an easier way... install nmap using apt-get, then run a scan on your subnet.

For example, if your LAN is 192.168.1.x, then you would do a:
```

nmap 192.168.1.*

```

and it will return a list of every IP that responds, and what ports are open.

Nmap can do far more than just this, though. [http://insecure.org/nmap/](http://insecure.org/nmap/)

---

