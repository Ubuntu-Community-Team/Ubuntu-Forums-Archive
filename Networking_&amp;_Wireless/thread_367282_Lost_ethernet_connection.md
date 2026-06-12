---
title: "Lost ethernet connection"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by t111 on 2007-02-22
I installed Ubuntu v6.1 a week ago.  I have always had a good
connection through my wired ethernet nic.   Today, all of 
the sudden I cannot connect.  The network manager sometimes
says that the ethernet connection is inactive and if I try to activate 
it, it fails and says I must check my connection or settings.
My settings are correct and I didn't make any changes to anything.
Sometimes the network manager says that my ethernet connection
is active but I still cannot connect to any web pages.  
I ran this command   "sudo ifup eth0" and I got this:

Internet Systems Consortium DHCP client v3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All Rights Reserved
For Info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

socket: Address family not supported by protocol - make sure 
CONFIG_PACKET (Packet Socket) and CONFIG_FILTER
(Socket Filtering) are enabled in your kernel 
configuration!
Failed to bring up eth0.

Does anyone know any way to clean this up?

---

### Post by gradedcheese on 2007-02-22
> 
socket: Address family not supported by protocol - make sure
CONFIG_PACKET (Packet Socket) and CONFIG_FILTER
(Socket Filtering) are enabled in your kernel
configuration!
Failed to bring up eth0.


ouch... well, this means DHCP won't work.  You could try assigning yourself a static IP, but I wonder about this error.  You are using a stock kernel, right?  Or have you built a custom kernel?  Also, please post the contents of your /etc/network/interfaces file.

---

### Post by t111 on 2007-02-22
> **gradedcheese said:**
> ouch... well, this means DHCP won't work.  You could try assigning yourself a static IP, but I wonder about this error.  You are using a stock kernel, right?  Or have you built a custom kernel?  Also, please post the contents of your /etc/network/interfaces file.

Thanks for the reply

I have uninstalled dapper and installed edgy so the problem is gone

---

### Post by zek725 on 2007-09-29
> **gradedcheese said:**
> ouch... well, this means DHCP won't work.  You could try assigning yourself a static IP, but I wonder about this error.  You are using a stock kernel, right?  Or have you built a custom kernel?  Also, please post the contents of your /etc/network/interfaces file.

using stock kernel (one with generic)

```

# This file describes the network interfaces available in your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
autolo
iface lo inet loopback

# The primary ntework interface
auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp





auto eth1


```

---

### Post by SpiritIsReality on 2007-09-30
howdy. 
please see this thread to see if it applies to you.
please post back and let everyone know how it's going/went
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
buds

---

### Post by SpiritIsReality on 2007-09-30
saw that gradedcheese was online and posted here to ask him to takeover.
my bad.

---

