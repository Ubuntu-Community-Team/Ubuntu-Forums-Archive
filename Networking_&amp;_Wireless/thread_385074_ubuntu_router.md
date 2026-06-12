---
title: "ubuntu router"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2007-03-15
Hi All, 

    For some reason, I am having difficulty setting up an edgy machine as a router. The machine has two network interfaces. eth0 for the LAN and eth1 for the internet. eth0 is connected to a LinkSys switch. The output of the route -n command for the edgy machine is given below:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.69.78.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0             192.168.0.1     0.0.0.0          UG    0      0        0 eth1

eth0 has ip address 10.69.78.1 and is running a dhcp server. eth1 has a ip address 192.168.0.101 and is connected to another router with IP address 192.168.0.1 which is connected to the internet . I have an ADSL network connection.

  From the edgy machine(server) I am able to ping [www.yahoo.com](www.yahoo.com). I replaced the LinkSys router conected to the server with another PC. I am able to ping 10.69.78.1 (the router) from that PC, but I cannot ping [www.yahoo.com](www.yahoo.com). It is not a problem with DNS since when I entered the ip address of [www.yahoo.com](www.yahoo.com), the result is the same.


I have no idea what the problem is. Any help would be really appreciated.

            - Jyothish

---

### Post by Mr. C. on 2007-03-15
See week 6 "Routing" notes and lab at : [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

