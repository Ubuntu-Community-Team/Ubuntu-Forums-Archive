---
title: "Problems changing port with Apache and Lampp"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by Nelson-Ray on 2007-09-17
Im gnashing my teeth here. I need to change apache's port, which is installed via LAMPP. I changed the listen line in httpd.conf from 80 to 85. I forward port 85 from the router to the static local ip address (192.168.1.90) of my LAMPP server. 

From within my lan i can type 192.168.1.90:85 and acess the webserver no problem.

When I try to acess the server from outside my lan, using the external ip address say 68.14.50.100:85 ... the web browser just stalls and then says cannot access 192.168.1.90:85 . 

What did I do wrong that makes the client computer from outside my lan pick up the internal lan ip (192.168.1.90:85) of the LAMPP server rather than its external ip (68.14.50.100:85)?

Any advice is greatly appreciated as I need someone to give approval on a web design before it gets implemented.

---

### Post by Brandon.Viking on 2007-09-17
Sounds like you have the port settings correct (because you can get to it locally)

Sounds like its more a routing or access control issue in the fact that you cant get to it from outside the lan.

iptables -L should show you the current firewall rules.
httpd.conf may be setup to only allow local lan by default ... look for "access" lines

Good luck .. hope that helps.

---

