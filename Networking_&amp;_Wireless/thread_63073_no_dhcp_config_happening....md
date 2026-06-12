---
title: "no dhcp config happening..."
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by monkotronic on 2005-09-06
i have a d-link nic card that is recognized ok by ubuntu install, but it times out when trying to get configured using dhcp.  i have a second computer that ubuntu did just fine with during install and it worked hassle free for the cable internet access.

i am hooked up to a router/cable modem directly.

now that ubuntu is installed, how do i install my nic?  i tried using the gui tools in both menus, but the options i need (ie configure and ethernet connection) are greyed out and not available.  

what are the command line tools i need to configure an ethernet card?  step by step would be helpful.  it would be helpful to know what i need to edit in order for it to be automatic from that point on.

THANKS, in advance...

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=monkotronic]i have a d-link nic card that is recognized ok by ubuntu install, but it times out when trying to get configured using dhcp.  i have a second computer that ubuntu did just fine with during install and it worked hassle free for the cable internet access.

i am hooked up to a router/cable modem directly.

now that ubuntu is installed, how do i install my nic?  i tried using the gui tools in both menus, but the options i need (ie configure and ethernet connection) are greyed out and not available.  

what are the command line tools i need to configure an ethernet card?  step by step would be helpful.  it would be helpful to know what i need to edit in order for it to be automatic from that point on.

THANKS, in advance...[/QUOTE]

The basic command line tools are "ifconfig" and "route".  The ifconfig command configures/activates/deactivates a network interface.  For example:
```
$ sudo ifconfig eth0 192.168.0.2
``` 
Activates interface eth0 and assigns it the (static) IP address 192.168.0.2.

The route command lets you set up your routing table.  You will at the very least need to set up a default route that tells where all network traffic needs to go (to your cable modem).
```
$ sudo route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.1
``` 
adds a default route that says to forward any packets that don't match any other routing rule to the gateway at address 192.168.0.1.

To make your changes permanent, you need to edit /etc/network/interfaces.

---

### Post by monkotronic on 2005-09-08
i'm using dhcp.  no static ip address available.  also no static dns available...all are assigned by comcast.

when i run:
   ifconfig eth0 dhcp start
i get the message: 
   hostname lookup failure
immediately.

any ideas?

---

### Post by s_p_a_r_k_y on 2005-09-08
try dhclient eth0

---

