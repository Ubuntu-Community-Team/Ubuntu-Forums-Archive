---
title: "apache + router  = no joy"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by tigerstripedcat on 2005-07-30
Router is a 9 dollar AirLink.  (Maybe this has something to do with it).

Without the router everything works fine.
SSH works fine even with the router, but apache does not.

/etc/hosts:


127.0.0.1       localhost.localdomain faye localhost
(faye is alias)


/var/log/apache/access.log
records requests, but seems to miss some requests

/var/log/apache2/error.log
nothing noteable

127.0.0.1 Will work 
192.168.1.101 will work (IP assigned by router wich detects MAC address and gives this assigned ip address)
128.XXX.XX.XX will not work
XXX.no-ip.com will not work

Things I've tried:
dhcpd
modifying etc/hosts
adding ServerName to apache2.conf

settings on the router that might be causeing the problem:

1)DHCP Server: currently enabled
2)Virtual Server (forwarding) forwards port 80 to 192.168.1.101
3)"Virtual Computers" global IP: 128.XXX.XX.XX LocalIP:192.168.1.101
4)MAC Address Control: routes MAC address 00-11... to 192.168.1.101 and 00-02... to 192.168.1.100

I've tried disabling 3 and 4.

My Conclusion:
1) Don't buy a 9 dollar router
or
2) There is still something I'm missing.  Could etc/hosts be the problem?  How should this be setup?

---

### Post by kosmic on 2005-07-30
There is problem with some cheap routers that can't do NAT with dinamic Ip's and can't also acess a DMZ zone if configured in the router, i've had the same problems with some routers from SIEMENS (with alcatel chip) and SMC.

The solution was to buy another router (router that works good -> lynksys, Cisco ;)

my 0.02 cents :)

---

