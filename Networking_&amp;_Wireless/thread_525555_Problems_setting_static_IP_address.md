---
title: "Problems setting static IP address"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by Dudsmacka2 on 2007-08-14
I have a box running ubuntu server edition that I use to run a Counter-Strike Source game server.  When I go to set a static IP address, as follows:

[INDENT][B]ifconfig eth0 10.0.0.5 netmask 255.255.255.0 up
route add -net default gw 10.0.0.1 dev eth0[/B][/INDENT]

The Counter-Strike: Source game server fails to find the master network (via the internet).  All other Internet functions (wget/apt-get/etc) still work.  I have no issues with the game server if I leave it on static IP address.

---

When I edit /etc/network/interfaces and do a **/etc/init.d/networking restart** I get the error message "ignoring unknown network eth0=eht0", with the following interfaces file:

[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.0.0.5
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        gateway 10.0.0.1
[/INDENT]

--

Was hoping somebody could point me in the right direction as to what I'm doing wrong.

---

### Post by larry007 on 2008-05-14
> **Dudsmacka2 said:**
> 

When I edit /etc/network/interfaces and do a **/etc/init.d/networking restart** I get the error message "ignoring unknown network eth0=eht0", with the following interfaces file:


Clearly you have some spelling issue here.....

eth0=eht0 - I presume that there is some typo in your /etc/network/interfaces - just double check.

---

