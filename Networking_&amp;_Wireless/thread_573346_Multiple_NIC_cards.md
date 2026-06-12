---
title: "Multiple NIC cards"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by reloded on 2007-10-11
Hi.

I have Ubuntu 7.04 server (no GUI)
Acer F5
3 NIC

I have been working using 2 NIC and everything was wonderful. I then added a 3rd NIC so as to create a DMZ. 
I already have eth0 and eth1 so I though I'd go to /etc/networking/interfaces and just add 


> auto eth2
iface eth2 inet static
        address 172.16.1.3
        netmask 255.255.255.0
        network 172.16.0.0
        broadcast 172.16.0.255
        gateway 172.16.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 172.16.1.7

Howerver, when I do that and restart the network,  ***/etc/init.d/networking restart*** I get
>  * Reconfiguring network interfaces...                                                                                                                       SIOCDELRT: No such process
SIOCADDRT: Network is unreachable
Failed to bring up eth2.

the command ***lspci ***shows
> 
02:11.0 Ethernet controller: MYSON Technology Inc SURECOM EP-320X-S 100/10M Ethernet PCI Adapter
02:12.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 25)
02:15.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)


So, how do I make the three NICs work together?

---

### Post by mpokrywka on 2007-10-12
You have an error in configuration:

address 172.16.**[COLOR="Red"]1[/COLOR]**.3
netmask 255.255.255.0
network 172.16.**[COLOR="Red"]0[/COLOR]**.0
broadcast 172.16.**[COLOR="Red"]0[/COLOR]**.255

Remove "network" and "broadcast" lines - they are unneccessary (computed automatically), and eth2 interface should work fine.

---

