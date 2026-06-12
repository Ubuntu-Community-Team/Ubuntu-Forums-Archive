---
title: "Ubuntu 16.04 share internet connection"
date: 2017-12-22
forum: Networking &amp; Wireless
---

### Post by Phelp on 2017-12-22
Hi, 

Is there a way in Ubuntu 16.04 to share internet with a second device:

i.e. getting internet from wificard and share internet over network (ethernet) card

assigning a specific address to the network card (in a way that could be seen as a gateway of choice

from the second device) ??

Even better if internet could be shared from a virtual machine running Ubuntu 16.04 with VirtualBox

configuring the network adapters !

Somebody told me that Ubuntu 17 could share internet (but I am working on 16 [17 looks like win8 to me))

and unfortunately when I try to use Ubuntu 17 as a virtual machine on VirtualBox I get problems 

with the installation of the virtualbox addons.


Thank You very much for any help


Bests 

P.

---

### Post by SeijiSensei on 2017-12-22
Any recent version of Ubuntu, or any other LInux distribution, can do this using the iptables functionality built into the kernel a decade or more ago.  Read [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

To install VirtualBox, I recommend following the procedure here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by Phelp on 2017-12-26
Hi thanks for the link.

I am using ubuntu 16.04 but from the gui network manager if I set up a "shared to other computers" connection the gui doesnt allow to choose the ip address  

as for example in the "manual" set up ?

tried to figure out something from 

**Simple iptables example**

 In a simple  example, wlan0 has the Internet connection, and eth0 is being used to  share the connection. It could be connected directly with a single  computer via a crossover cable or switch, or you could have a router  with a cable from eth0 to the WAN port and a whole LAN setup behind  this. Interestingly, the Internet connection could be ppp0, a 3G, or  mobile Internet modem. 
#!/bin/sh 
 # 
 # internet connection sharing wlan0 is the gate way 
 # eth0 is the lan port this might use a straight ethernet cable to a router wan port or a switch or a single PC
 # 192.168.2.2 is the port  that is being used by the lan for access I changed it to 192.168.2.254  and set fixed addresses for the wan and router
 #
 # change wlan0 to ppp0 and you can use this for mobile broadband connection sharing
 #
 ip link set dev eth0 up
 ip addr add 192.168.2.1/24 dev eth0
 sysctl net.ipv4.ip_forward=1
 iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
 iptables -t nat -A PREROUTING -i wlan0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.2.2
 iptables -t nat -A PREROUTING -i wlan0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.2.2
 iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p tcp --dport 3074 -j ACCEPT
 iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p udp -m multiport --dports 88,3074 -j ACCEPT


but to mee its rather uncomprensible ? any link to a idiot proof page about iptables

the script above give me  a lot of errors (I amn using iptables 1.0.6)


will this simpler one work too ?? :  (eth0 is the card connected to internet to be shared to card eth2)

ip link set dev eth2 up
    ip addr add 192.168.16.16/24 dev eth2
    sysctl net.ipv4.ip_forward=1
    iptables -t nat -A POSTROUTING -o eth0 -s 192.168.16.0/24 -j MASQUERADE
    iptables -A FORWARD -i eth0 -o eth2 -m state --state RELATED,ESTABLISHED -j ACCEPT
    iptables -A FORWARD -i eth2 -o eth0 -j ACCEPT

Thank You a lot

Bests

P

---

