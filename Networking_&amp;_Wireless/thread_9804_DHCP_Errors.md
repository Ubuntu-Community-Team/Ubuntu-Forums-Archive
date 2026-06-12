---
title: "DHCP Errors"
date: 2005-01-01
forum: Networking &amp; Wireless
---

### Post by prionux on 2005-01-01
Hello everyone,

I recently moved to college and thus changed ISPs. With my old ISP (Bellsouth), DHCP and everything else worked fine. Now, when I try to set up my connection I get these messages from ifup and ifdown:

ifup:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Operation not supported.
    Internet Systems Consortium DHCP Client V3.0.1rc14
    Copyright 2004 Internet Systems Consortium.
    All rights reserved.
    For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

    Listening on LPF/eth0/00:d0:09:75:25:98
    Sending on   LPF/eth0/00:d0:09:75:25:98
    Sending on   Socket/fallback
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
    DHCPOFFER from 209.90.120.129
    DHCPREQUEST on eth0 to 255.255.255.255 port 67
    DHCPACK from 209.90.120.129
    SIOCADDRT: Network is unreachable
    bound to 209.90.73.213 -- renewal in 9032 seconds.

ifdown:

Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:d0:09:75:25:98
Sending on   LPF/eth0/00:d0:09:75:25:98
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 209.90.120.129 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.


Again, everything was working before so I know my Ethernet card is working correctly. Plus everything works fine in Windows (shocking). I've fiddled around with the settings in network-admin but that doesn't help anything. If I try to ping anything I just get a "Network unreachable" message. I've tried using the 2.6.9 kernel to see if that would help at all but no luck. Any help or suggestions would be greatly appreciated.

---

### Post by forkbeard on 2007-02-05
I'm running Edgy on my G4 iBook and I'm getting the same errors.

I can connect fine at the university (presumably because this was the first place that I connected to a network) but as soon as I take it home and try to connect to my home network, over wired or wireless connections, it never picks up on the DHCP server.

---

### Post by gradedcheese on 2007-02-06
"Error for wireless request "Set Encode" (8B2A) :
SET failed on device eth0 ; Operation not supported."

This is not a DHCP error, what's actually happening is that "set encode" is being attempted on eth0, which it does not support.  Is eth0 an Ethernet card but it's being treated as a wireless card?  Or is eth0 really a wireless card?  I would check your /etc/network/interfaces file and make sure that everything there makes sense (or post its contents here if you need help).  You can then bring the specific device up or down or, if you're confident that /etc/network/interfaces is filled out correctly:

sudo /etc/init.d/networking restart

dhclient is the DHCP client, it's called after the networking interface is set up.  If setup failed, then dhclient will also fail.

---

