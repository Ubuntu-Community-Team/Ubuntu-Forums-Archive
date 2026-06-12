---
title: "IPv6 only network with IPv4 Link local and IPv6 default route lost"
date: 2018-12-19
forum: Networking &amp; Wireless
---

### Post by indra77 on 2018-12-19
Hello Everyone, 

My Current Project i am faced with IPv6 only network and below are some of the problems i am encountering with Ubuntu 16.04 running on Samsung Artik board (hardware).



[LIST=1]
[*]Ubuntu 16.04 OS is assigned IPv6 address from Network over SLAAC protocol. ETH0 is the network interface which has IPv6 Link and Global address. But on OS boot, ETH0 Interface gets Link Local IPv4 (169.254.x.x) address which also creates an entry in IPv4 routing table which we do not want.
[LIST=1]
[*]As per my reading, Link Local IPv4 address is assigned , when DHCP Client tries to find DHCP server but fails and automatically assigns an IPv4 address which can be used to communicate with other host over local network. Basically, this is called _APIPA( Automatic IP Addressing) and we would want to disable this in Ubuntu 16.04 OS_
[LIST=1]
[*]Steps tried so far is to disable avahi-daemon , change avahi configuration but still IPv4 (link local) keeps getting assigned to ETH0 interface.  The same is removed by issuing command ifconfig eth0 0.0.0.0.
[/LIST]
[/LIST]

[*]It can be observed that IPv6 default route is not set in Ubuntu 16.04 OS. This is checked by issuing command ip -6 route show | grep default.  Here, I was unable to identify the Root cause as to which entity in Linux kernel (network) is responsible to set the default IPv6 route.
[LIST=1]
[*]To overcome the above problem, I had to restart networking service using (/etc/init.d/networking restart). But after a given time interval default IPv6 route still disappears from IPv6 routing table.
[*]It is also observed,  on system reboot or after manually restarting networking service, DNS server address is not populated in /etc/resolv.conf file. Applications then fail to resolve web addresses.
[/LIST]
[/LIST]

Questions :
 

[LIST]
[*]Which service (or background process) is responsible for setting / removing Default IPv6 route in Ubuntu 16.04 ?
[*]Which service (or background process) is responsible for assigning IPv4 link local address to ETH0 interface at periodic intervals ?
[*]Which service is responsible for writing DNS address in /etc/resolv.conf file and when will it do the same ?
[*]Given that above 3 entities are identified, can we control their behavior or it is completely dependent on Messages received by Network router ?
[/LIST]

Any Pointers will be greatly appreciated.

---

