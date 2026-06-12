---
title: "How do I find ip address with a router assigning dhcp"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by erkker on 2007-01-29
Hello all,

I am new at this game, but I have a wireless router connected to my main box  (Edgy Desktop) and a almost un-configured  edgy server which also broadcasts internet to my two roommates.

I want to keep my router (linksys wrt54g) running dhcp for the network because I dont want to become the system admin for the apartment (both roomates have macs of various flavors).  With the router running dhcp I cannot configure a static ip address in /etc/network/interfaces because the router apparently overrides the configuration file.  

Which would be fine but...

I want to ssh into my server.  Is there an easy way to search the ip addresses assigned on my network?

Thanks everyone

-E

---

### Post by Stephen Howard on 2007-01-29
Lots of routers let you specify a static IP & hostname based on MAC device numbers.  Once configured, you're guaranteed that any time a unit with a specific MAC number appears on the network the router will assign it the same IP address and hostname.  Might be worthwhile checking if that option is available on your router.

---

