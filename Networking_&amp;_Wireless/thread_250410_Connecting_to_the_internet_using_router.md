---
title: "Connecting to the internet using router"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by ofer_w on 2006-09-04
The computer with ubuntu is connected to router and the router is connected to the internet.

What it should be set up in ubuntu in order to get the internet working?

Thank you

---

### Post by amo-ej1 on 2006-09-04
Well if it's one of those small and home office (wireless routers) like the a  standard wrt54g, it should simply be connected to the internet and have dhcp configured (allowing your other pc to get a dhcp lease, by default this should work out of the box, but some can filter based on mac addresses). Next you should have your ubuntu system make use of dhcp (which should be done by default). And thing should like ... just work ...

What have you tried already ? And how does you network setup look like ?

---

### Post by amo-ej1 on 2006-09-04
initial tests might be:

a) are cable connected properly
b) are the link detected led's working ?
c) does 'ethtool eth0' (if eth0 is your interface) show a detected link ? 
d) did your ethernet interface receive and IP address (when using dhcp, 'ifconfig eth0' 
e) can you ping the (internal) ip address of the router ?
f) can you resolve dns (try ping [www.ubuntuforums.org](www.ubuntuforums.org) does this translate to the correct ip address  ?
g) can you run a traceroute/mtr to and external site  (traceroute [www.ubuntuforums.org](www.ubuntuforums.org) )

---

### Post by ofer_w on 2006-09-04
> **amo-ej1 said:**
> initial tests might be:

a) are cable connected properly
b) are the link detected led's working ?
c) does 'ethtool eth0' (if eth0 is your interface) show a detected link ? 
d) did your ethernet interface receive and IP address (when using dhcp, 'ifconfig eth0' 
e) can you ping the (internal) ip address of the router ?
f) can you resolve dns (try ping [www.ubuntuforums.org](www.ubuntuforums.org) does this translate to the correct ip address  ?
g) can you run a traceroute/mtr to and external site  (traceroute [www.ubuntuforums.org](www.ubuntuforums.org) )

a) the cable is connected properly
b) the link is green in the router
c) there is error messege :
setting for eth0:
cannot get device setting: operation not permitted
can not get message level : operation not permitted
can not get link status: operation not permitted

probbly need to be root but don't know the password
d) is working there are few lines 
inter address: 10.0.0.2  Bcast:10.255.255.255 Mask:255.0.00
f) ping is not working
g) not sure what to write 
you mean : traceroute/mtr [www.ubuntuforums.org](www.ubuntuforums.org)
?

---

### Post by amo-ej1 on 2006-09-04
are you using dhcp ?  what is the ip address of your router ? what is the output of 'arp -a'

traceroute won't work if your ping doesn't work ;-)

---

