---
title: "Proxy-arp settings for multiple network cards"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by WWWXXX on 2013-09-11
Hi all:

I am new to ubuntu, currently we got a linux machine with Ubuntu 12.04 which has three network cards plugged inside, and I would like to make eth0 and eth1 can get own ip and surf internet, as shown in the figure.

       |
       | eth1
    +-------+
    |Linux  |-------
    |     PC      | eth0
    +-------+
      |
      | eth2
      | to internet
      |
 ----|---|--------|----


I have a friend who gave me some comments:
a.       2 interfaces with eth1, eth0 would be proxy-arp’d on to 3[SUP]rd[/SUP] network
b.      Change rc.local file to add 2 arp table entries for eth0, eth1
c.       Eht2 to the internet
d.      Set route commands in rc.local to forward packets to the 2 machine on eth0 and eth1
e.      A proxy dhcp server on main machine for eth0 and eth1

But sadly I have no experience about network setup, also proxy settings. 
Could anyone kindly teach me how can I set up or what commands I may need?

Many thanks.

---

### Post by WWWXXX on 2013-09-12
Or make simpler, ignore eth1 how can I set, so that eth0 can have its own IP and access to the internet?


Thanks.

---

### Post by s-bodet on 2013-09-14
Hi,

If you want the eth0 & eth1 IP subnets to access the Internet, you just need to enable SNAT in your server.
Pretty sure Google will help :-)

Steve

---

