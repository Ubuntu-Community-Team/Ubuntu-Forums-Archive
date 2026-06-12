---
title: "Migrating web server to another IP"
date: 2014-01-27
forum: Networking &amp; Wireless
---

### Post by avaserver on 2014-01-27
Hello there.
I have a little problem. 
I installed Ubuntu Server 12.04 + LAMP + EHCP (control panel). 
When changing my fixed IP (after upgraded my internet connextion and purchase a subnet /29), what changes should I make to my DNS server?
I already have 35-40 sites hosted on my server. 


I mean, besides eth0 configuration (in  /etc/network/interfaces), disabling pppoe, I guess it is necessary to modify all zones from BIND with the new IP address? 
It is also necessary to change the forwarders from /etc/bind/named.conf.options  and set the new IP address in TLD?

Thanks in advance !

---

