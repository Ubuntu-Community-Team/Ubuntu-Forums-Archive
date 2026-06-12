---
title: "Can't ping or connect to Ubuntu server hostname"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by SnowPunk98 on 2007-02-22
I have set the hostname on the machine as well as a static IP address but I am unable to ping or connect to it via the hostname. Do I have to install DNS on the server or do something else to the server or add it to the hosts file in my Windows machine?

What would be the equivalent to a hosts file in Linux to make the same changes if thats what I need to do.

---

### Post by gradedcheese on 2007-02-22
> 
Do I have to install DNS on the server or do something else to the server or add it to the hosts file in my Windows machine?


Yes, you do.  Otherwise, no one is providing host_name->IP mapping (A-records) on the network, right?  Add the machine to the Windows PC's hosts file.  There's a similar file in Linux, to which you should add the Windows PC's host name: **/etc/hosts**

If you don't want to do manual updating of the hosts files, then you need a DNS server or (alternately) an mDNS service via Avahi.

---

