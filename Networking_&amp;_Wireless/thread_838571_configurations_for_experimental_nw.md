---
title: "configurations for experimental n/w"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by ub007 on 2008-06-23
Hi,

I'm trying to setup an intranet within my university network for tesing and learning use.at the moment,i got 3 PCs and a switch.I've installed ubuntu server on one PC and this machine is connected to the internet.I intend to have the other 2 PCs(ubuntu again) to act as clients to the server.
-I would like to have the server lease out ip addresses to the 2 Desktops.(dhcp)
At the same time i do not want the server dhcp to mess up with the uni network.... 
Also need to ensure the clients access the server locally and not via the internet....
How do i configure the dns and dhcp(both client& server)to accomplish this?do i need to configure the switch as well or just plug the 3 comps into it...?or do i have to use the switch at all?...totally confused.....

Cheers
Davis

---

### Post by Rocket2DMn on 2008-06-23
Related to: [http://ubuntuforums.org/showthread.php?t=838518](http://ubuntuforums.org/showthread.php?t=838518)
Essentially you will have to have your server get an IP from the university network and then configure the other machines to use the server as the DHCP server.  This will require some software on the server as well.  I will request that a mod move this thread to the Networking forum so you can get better help with your problem.

---

### Post by ub007 on 2008-06-23
thanks mate,
i will paste this as a new thread in the n/w forum...
my supervisor asked me to unplug it from the uni n/w once dhcp is started and thats y he provided me with the switch....however i cant access the internet if i unplug from the uni n/w n also tryn to find an alternative to accomplish both tasks...

cheers

---

### Post by Sef on 2008-06-23
Moved to Networking and Wireless.

---

