---
title: "How to setup a normal user to use ports less than 1024"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2008-01-22
Hi 

I am trying to figure out a way to allow a non-root user to use sockets lesser than 1024. From what I have read so far this seems to be possible using Linux Capabilities (CAP_NET_BIND_SERVICE). How can I give this capability to a non-root user. ?

Why do I need this to work - I have a client whose servers I can access only through the VPN provided by Juniper Networks which runs on a browser and uses Java applets. Following is from their documentation 

***"Automatic editing of hosts file and ports less than 1024 are available only for root users."***

The only way i was able to run it so far was to run firefox using gksudo.

Any help in this regard will be really helpful. I will need to revert back to using Windows if I cant get this running on Linux. 

Thanks much.

---

### Post by kirsche on 2008-01-22
The host file should only be touched if you use split tunneling and access the remote sslvpn by FQDN (just as a side note)
Depending on the access method you want to use (NC, JSAM, CORE), the remote admin can define a client side port.
Apart from that - can you live with sudo?

---

