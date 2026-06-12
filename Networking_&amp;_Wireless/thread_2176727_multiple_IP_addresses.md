---
title: "multiple IP addresses"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by michael-h-williamson on 2013-09-25
Hi, 

I used the networking configure GUI on ubuntu 12.04 to add a second IP address to a working ethernet port.
The new address is accessible from the local network, but not from the outside world, using ssh, ping, etc.
 Then I deleted it, and assigned it instead to a additional hardware ethernet port in the same computer.
But still the same result, only local network access is possible.

Does anyone know what is the problem?

netmask 255.255.255.0
gateway xxx.xxx.xxx.1

Thanks,
-Mike

---

### Post by 7182818 on 2013-09-25
What is your network setup like?  Are you behind a wireless router or a firewall?

---

### Post by michael-h-williamson on 2013-09-26
I am not using a wireless router, or a firewall for the local network. 
The computer firewall is disabled too. 

Note that the original IP address remains functional from outside the local network.
Only the second IP is not responsive beyond the local network. The local
network is allocated 255 addresses, and has approximately 50 computers in use.

---

### Post by 7182818 on 2013-09-26
Hmm, I wonder if something is going wrong from a routing perspective.  Are the IPs on both interfaces in the same subnet?  Out of curiosity, does using the second IP address work if you configure it on the first interface?  For example, if your first interface is eth0 with IP 1.1.1.100, try 'sudo ifconfig eth0:1 1.1.1.101 netmask 255.255.255.0' and then see if you can ping 1.1.1.101.

---

### Post by michael-h-williamson on 2013-09-26
I implemented your suggestion, Hockeyplayer363, and that resolved the problem. With the configure GUI, I reassigned the IPs, reversing the numbers for the hardware ports, and then 'service network-manager restart', and it works. I have no explanation why that solved the problem. Thanks. (How do I indicate that the issue is solved in the summary of this thread?)

---

