---
title: "Network problem 2 NICs"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by jax2000 on 2006-09-06
Hi,

I hope someone could help me with my problem. I have a FTP server which is connected directly to DSL box and also directly to Firewall.

eth0 -> DSL (static ip 195.197...)
eth1 -> Firewall (static ip 192.168.0....)

My goal is to have FTP server that is accessed from outside our LAN (eth0) and also available to our LAN computers (eth1) 

I have all this set up but whenever I activate the eth1 NIC network dies and I can't browse the web and nothing, nobody can access our ftp server. Is it possible to have this kind of setup so it will not get messed up when both cards are active

---

### Post by tbonius on 2006-09-06
Maybe I am not understanding the setup.. but are the two NICs necessary for your network?  Are you using the Linux box as a NAT/FIrewall gateway?  Make sure you do not have default gateways defined for each NIC.  You might only need the external NIC connected to your DSL router to have a default gateway defined.

T

---

### Post by jax2000 on 2006-09-18
> **tbonius said:**
> Maybe I am not understanding the setup.. but are the two NICs necessary for your network?  Are you using the Linux box as a NAT/FIrewall gateway?  Make sure you do not have default gateways defined for each NIC.  You might only need the external NIC connected to your DSL router to have a default gateway defined.

T

Hi, How do I remove the default gateway for the second card? Cant do it in network-admin. 

My setup is <-- DSLBOX <--eth0--> UBUNTU SERVER <--eth1--> FIREWALL <-- OTHER COMPS

---

### Post by Original Brownster on 2006-09-18
Hi,
Sounds like your eth1 card is using dhcp? If you are you need to modify the way the card eth1 recieves info from the dhcp server, I hadn't done this before but found that you can modify your /etc/dhcp3/dhclient.conf file to include a stanza for a particular card and say exactly what info you want from the dhcp server. In this case you don't want a default gw for eth 1 so remove the option 'routers' from the newly created stanza for your eth1 card, here's an example for you as I was messing about with it (take a copy of the file before you start tinkering ;-) ):

> 

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

[COLOR="Red"]interface "eth1" {[/COLOR] request subnet-mask, broadcast-address, time-offset,
        domain-name, domain-name-servers, host-name,[COLOR="Blue"] routers,[/COLOR]
        netbios-name-servers, netbios-scope;[COLOR="Red"]}[/COLOR]


See the stanza I added for eth1 ? Remove the word and comma 'routers,' which I've highlighted blue. 
Restart the network:
$ sudo /etc/init.d/networking restart

check what default gateways are defined:
$ route

> **jax2000 said:**
> Hi, How do I remove the default gateway for the second card? Cant do it in network-admin. 

My setup is <-- DSLBOX <--eth0--> UBUNTU SERVER <--eth1--> FIREWALL <-- OTHER COMPS

---

