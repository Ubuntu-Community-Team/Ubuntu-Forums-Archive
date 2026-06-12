---
title: "Can't detect second NIC"
date: 2005-05-26
forum: Networking &amp; Wireless
---

### Post by rivaitan on 2005-05-26
Hey guys, I'm trying to set up an office network with ubuntu. I managed to get things going with the first nic card, shared folder and printing and all. Now I jacked in a second NIC card into the server station hoping to enable internet access on the workstations, well, ubuntu ain't detecting it. Any help? 
The card's thats undetected is a linksys instant etherfast 10/100 lan card. LNE100TX

Thanks fellas

---

### Post by bmgz on 2005-05-26
try "sudo modprobe tulip"...

---

### Post by bmgz on 2005-05-26
[QUOTE=bmgz]try "sudo modprobe tulip"...[/QUOTE]
 you may first need to set an alias for eth1 in /etc/modprobe.d/aliases:
alias eth1 tulip

..and you will need to find out how to configure "ip masquerading" if you want other machines to access the internet through your machine..

---

