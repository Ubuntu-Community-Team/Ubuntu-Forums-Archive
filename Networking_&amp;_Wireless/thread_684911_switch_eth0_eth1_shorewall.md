---
title: "switch eth0 eth1 shorewall"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by Rick Z on 2008-02-01
Hi

I am trying to setup a router (dhcp3-server & shorewall 3.4.x installed).

My reason to post this is because shorewall will recognize eth0 as external NIC which connect to ISP.  This works out perfect if I have ISP modem directly connect to my eth0 and use eth1 as DHCP server to work as router.

What I want to do is use a spare laptop with wireless (eth1, as external source that connect to ISP.  In this case, connect to my wireless router) and wired NIC (eth0, as the DHCP server to my other LAN) to setup as a router (or Access Point) similar to my other system.  

How would I accomplish this?  I believe shorewall will ‘only’ use eth0 as external NIC, but I might be wrong.  How can I make the shorewall recognize that eth1 is the external source?  Someone please enlighten me with the setting in shorewall.

The other possibility might be is that I change the name of the eth0 & eth1 right?  If so, how do I do this?  I found a command called ‘nameif’, but I couldn’t get it to work.

Thanks.

---

