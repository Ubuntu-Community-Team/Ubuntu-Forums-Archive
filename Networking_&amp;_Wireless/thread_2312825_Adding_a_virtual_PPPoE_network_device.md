---
title: "Adding a virtual PPPoE network device"
date: 2016-02-07
forum: Networking &amp; Wireless
---

### Post by Endlesskiss on 2016-02-07
Hey everyone!

I'd like to make some experiments on PPPoE.

My setup is as follows: Fedora as a host, with VMWare workstation installed.
Ubuntu 15.10 VM as guest.

The ubuntu, via LAN, shares the internet connection with the Fedora.

I'd like to add a PPPoE device on the ubuntu, so it would be possible to see it on /sys/class/net/pppoe and /sys/class/net/pppoe/type would return 512 (which is [ARPHRD_PPP]("http://lxr.free-electrons.com/ident?i=ARPHRD_PPP") as defined in if_arp.h)[COLOR=#787878][FONT=Monaco][/FONT][/COLOR]I've read some tutorials regarding pppoe-server but when I tried configuring everything (and setting the interface to be enoXXXXXXX, which is the NAT interface for the internet connection) the server simply exited immediately.


The PPPoE device should be bridging everything to the internet connection, therefore it should react as a gateway to the NAT interface.


The most updated tutorial I could've found on the internet is this: [http://www.howtodoityourself.org/pppoe-server-how-to-do-it-yourself.html](http://www.howtodoityourself.org/pppoe-server-how-to-do-it-yourself.html)

Unfortunately, the /sys/class/net/ppp0 device lasts for as long as the client attempts to connect to the server, which is, as I've said, exists immediately.
The client then receives a timeout and exists, and the /sys/class/net/ppp0 device disappears.

I don't have a PPPoE username and password but as it runs under VMWare I can configure easily new network adapters (if necessary).


I would be grateful if someone could shed some light on the issue.


Sincerely,
Adam.

---

