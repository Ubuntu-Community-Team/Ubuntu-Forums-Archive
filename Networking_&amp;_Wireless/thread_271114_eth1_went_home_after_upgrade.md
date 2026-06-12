---
title: "eth1 went home after upgrade"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by 3200 on 2006-10-04
I've been combing the threads and have seen similar threads, but the fixes don't seem to help.  I upgraded my nVidia driver on an Ubuntu 6.06 system and completely lost my eth1 configuration.  Now, the machine sees the wireless card AND the driver, but the eth1 isn't configured.  How do I do that?  Here's what I've done and what the output has been:

$ sudo ndiswrapper -l
> Installed ndis drivers:
netw39x5                driver present, hardware present


$ sudo ifdown eth1
> ifdown: interface eth1 not configured

$ sudo ifup eth1
> Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

I can post the interface file too:
> 
# The loopback network interface
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet dhcp
wireless-essid <essid>
wireless-key <key>


auto eth0
iface eth0 inet dhcp


Please keep in mind, I am so new to Ubuntu and Linux, I look for kernels in a cereal box... :)

---

### Post by 3200 on 2006-11-02
BUMP.

Any help on how to configure the eth1?  Anyone...?

---

### Post by bmuni on 2006-11-02
Did you try System-->Administration-->Networking? Try re-configuring the card again. Then you need to make sure the card is active. Do ifconfig -a, and you should see eth1 come up with an ip address.

---

