---
title: "2 Interfaces, Direct Traffic"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by ninocass on 2007-05-18
Hey all, can someone help with this one:

I have 2 NICs in my lappytop one wired and one wireless.

I currently have the wired connected to a network that has no internet connection.

I also have the wireless card connected to the wireless this has internet.

If i do "ping -I eth0 10.0.0.2"  it will ping the 10 network

if i do "ping -I eth1 192.168.1.1" it with ping the 192. network

The problem is when i want to use a program that does not allow me to define an interface ie firefox nmap etc etc

Any ideas?

Cheers

Nino

---

### Post by ninocass on 2007-05-18
I found this post:

[http://ubuntuforums.org/showthread.php?t=383488&highlight=NIC](http://ubuntuforums.org/showthread.php?t=383488&highlight=NIC)

> 
For example:
eth0
Address 192.168.0.10
Netmask 255.255.255.0
Gateway 192.168.0.1

eth1
Address 192.168.1.10
Netmask 255.255.255.0

With this configuration, you'll get 3 routes:
To the 192.168.0.x network, via eth0
To the 192.168.1.x network, via eth1
To any IP address not in the 192.168.0.x or 192.168.1.x range, to the gateway at 192.168.0.1, via eth0


im assuming this is in the interfaces file?  mines appears to be empty :S

---

### Post by spd106 on 2007-05-18
You don't say whether you are using network manager or any other app that invokes DHCP. If you are using DHCP then your wireless interface should be assigned an default gateway. 

If you setting a static configuration then you will need to specify a gateway. You might want to read up on routing in Linux, try this guide [http://tldp.org/HOWTO/Adv-Routing-HOWTO/](http://tldp.org/HOWTO/Adv-Routing-HOWTO/)

---

### Post by ninocass on 2007-05-18
Sorry yes im using DHCP on both of the interfaces and the "wireless configuration namager" to joing with the wireless network

ill give that guide a read

Thanks

nino

---

### Post by netztier on 2007-05-18
> **ninocass said:**
> Sorry yes im using DHCP on both of the interfaces and the "wireless configuration namager" to joing with the wireless network

ill give that guide a read


Using DHCP on both interfaces, *both* DHCP servers will (most certainly) give default gateway information, so your routing table will probably end up with two default route entries. Bad thing, as "there can only be one" ;-). The one that comes first in the table will take precedence over the other - and that might be the "wrong" one. 

Same risk is with DNS servers. To some degree of probability, both DHCP servers will tell your PC which DNS servers to use. This information will be written to the file **/etc/resolv.conf**, and it might be that the wrong one ends up in there as the first.

With both interfaces connected and up, do a **netstat -nr** and post the output here, please, as well as the content of **/etc/resolv.conf**.

Possible solution: configure one interface with a static IP address (without gateway information), the other with DHCP, including DNS and default gateway information.

Alternative: tweak DHCP client configuration for one of the interfaces not to request (nor accept) default gateway and DNS information.

best regards

Marc

---

