---
title: "Proxy severs"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by andyprice on 2007-08-07
Hi, I`m just trying to learn how to do this, but I can`t seem to enable the dhcp client on my proxy server.  When I attemt to start the server, the meeage I get is below....Help

Any advice would be great.

Andy

Failed to start dhcpd :

dhcpd self-test failed. Please fix the config file.
The error was: 
/etc/dhcp3/dhcpd.conf line 106: subnet 127.0.0.1 netmask 255.0.0.0: bad subnet number/mask combination.
subnet 127.0.0.1 netmask 255.0.0.0 
                                 ^
/etc/dhcp3/dhcpd.conf line 115: expecting key name.
	key ;
        ^
Configuration file errors encountered -- exiting

---

### Post by fazavon on 2007-08-07
This is the best answer I can find for you, with out give you a crash course in networking.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#DHCP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#DHCP_Server)

//j

---

