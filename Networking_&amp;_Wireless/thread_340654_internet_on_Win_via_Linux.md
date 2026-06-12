---
title: "internet on Win via Linux"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by dujlinvik on 2007-01-17
greetings,
i had been looking for an answer to my question on some forums, but....
i wonder if SAMBA can be suitable for internet sharing, or it just provides file/print sharing services... Namely, i want to use/share an internet connection on two machines:
1. Linux Ubuntu - configured pppoe connection to the web through a wireless network
2. Windows XP - client
can somebody tell me which program do i need to install/configure?
THANKS

---

### Post by vmikalinis on 2007-01-17
Samba can only function as a file, time, and print server in conjuction with other services.  It doesn't rpovide internet connection sharing.

I would suggest going out and getting a cheap hardware wireless router/firewall.

---

### Post by Garyu on 2007-01-17
You will need to setup linux to run as a DHCP server for your windows machine. If you search the forum or wiki for DHCP you should be able to find a few tutorials. Just find one that matches your needs the best. 

Another more interesting option is to switch to IPv6 on your LAN, using linux as a router with IPv6 tunneling. This requires a lot of work though, but will put you on the cutting edge. ;-)

Things to look at if you don't know what to search for:
[http://doc.gwos.org/index.php/ServerGuide#Dhcpd](http://doc.gwos.org/index.php/ServerGuide#Dhcpd)

[http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/](http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/)

---

