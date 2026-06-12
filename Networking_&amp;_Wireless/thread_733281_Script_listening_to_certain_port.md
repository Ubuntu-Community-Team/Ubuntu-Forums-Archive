---
title: "Script listening to certain port"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by meskola on 2008-03-23
I have a couple of scripts that generate some statistics.

Now I would like to have these scripts accessed remotely rather than locally.

I have earlier done this in solaris where I only needed to add them into /etc/inetd.conf and /etc/services and restart inetd.

Now on my Ubuntu box neither inetd or xinetd is running (at least according to ps) but all networking services are running as they should.

Do I need to add inetd or can I use whatever Ubuntu comes with out of the box and in that case how do I get my apps started when a certain port is accessed?

BR
Markus

---

