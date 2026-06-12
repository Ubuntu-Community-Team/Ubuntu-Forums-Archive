---
title: "Problems with dhcp3-server"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by MattiViljanen on 2005-11-03
Hi

Anyone tried to configure Ubuntu 5.10 as a dhcp server? Also, I'm trying to make "thin client" boot possible from LAN. I have gone through [this]("https://wiki.ubuntu.com/ThinClientHowto") guide, but I just can't follow the guide, because the dhcp3-server service fails to start:
(the command used is "sudo /etc/init.d/dhcp3-server restart"

> 
 * Stopping DHCP server... [fail]
 * Starting DHCP server... [fail]


There's INTERFACES="eth0" in /etc/default/dhcp3-server and the eth0 interface is configured to use a static IP address (10.10.42.3, that is). I've also added "auto eth0" to /etc/network/interfaces file.

I'm stuck!

---

### Post by mips on 2005-11-03
I have a dhcp server running on my box to serve a windoze PC. 

I'm not using dhcp3-server.

I use dhcp v2.opl5-19.1 package from synaptic. Configured via firestarter.

---

### Post by mgor on 2005-11-03
have you added any scope of IP adress for the dhcp server to hand out?
check [https://wiki.ubuntu.com/Installation/LocalNet](https://wiki.ubuntu.com/Installation/LocalNet)

---

### Post by Peter76 on 2005-11-03
The same happened to me, look at the syslog, that gave me the clue, in other words, you need to set up your /etc/dhcp.conf for your nics. See man dhcp.conf how to set this up. Good Luck

---

### Post by MattiViljanen on 2005-11-04
dhcpd threw this to syslog:

> No subnet declaration for eth0 (10.10.42.3).
Please write a subnet declaration in your dhcpd.conf file for the
network segment to which interface eth0 is attached.
exiting.

Well, I think Firestarter came up with a solution: I have to install two network cards.

I'm trying that now...

PS. Now I'm thinking about installing a proxy server as well :KS

---

### Post by MattiViljanen on 2005-11-04
Yep, that did it. I only needed two network cards. Guess the same thing was the issue with dhcp3-server, too...

Thanks, mips, for pointing me a program that told me what was wrong ;)!

---

