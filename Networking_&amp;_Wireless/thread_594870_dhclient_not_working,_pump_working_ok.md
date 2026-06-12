---
title: "dhclient not working, pump working ok"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by plaa on 2007-10-28
Hi,

I have finally solved a problem with dhcp using a WLAN card on my Thinkpad laptop.  The symptoms of the problem seem identical to the ones reported by others when using a Thinkpad in [*this thread*]("http://ubuntuforums.org/showthread.php?t=315236&page=9").  I posted my findings there also, but I got no replies.

In many cases, either dhclient doesn't receive a dhcp reply from the wlan router or ***it receives a reply but doesn't do anything!***  On my university wlan network (open wlan, no WEP or other encryption) I often have dhclient receiving a reply with all necessary information, but it doesn't do anything with it.  Below is a typical output of dhclient when run manually (automatic doesn't work either):

```
# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 10930
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:02:2d:08:d1:d5
Sending on   LPF/eth1/00:02:2d:08:d1:d5
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 130.233.238.254
bound to 130.233.238.150 -- renewal in 561 seconds.
#
```

I have intercepted the dhcp transfer using wireshark and received the following packets going to and from the router (all other network traffic except the DHCP packets have been filtered away): [http://eddie.dy.fi/~sampo/dhcp/dhclient-dhcppackets](http://eddie.dy.fi/~sampo/dhcp/dhclient-dhcppackets)  

When analyzing the packets, dhclient has sent a DHCP Request and received a DHCP ACK, which contains all the necessary network information (the IP mentioned above, gateway, nameservers etc).  However, when using ifconfig afterwards no IP is assigned to eth1, no name servers are listed in /etc/resolv.conf and route -n shows an empty routing table.

On the other hand, if I run pump with pump -i eth1, it receives the IP and sets all settings normally, and the network works automatically.  The captured packets when using pump are available at [http://eddie.dy.fi/~sampo/dhcp/pump-dhcppackets](http://eddie.dy.fi/~sampo/dhcp/pump-dhcppackets) .  First pump sends a DHCP Discover, which is replied to with a DHCP Offer, then it again sends a DHCP Discover, which is replied to, and then pump sends the DHCP Request and is given a DHCP ACK with the necessary settings.

I noticed this to work when I tried the WLAN with Knoppix and it worked instantly (Knoppix uses pump instead of dhclient), but I had no luck using Ubuntu Feisty or Gutsy.  I am not sure whether this is an issue only in Ubuntu or dhclient in particular.  It seems to be somehow hardware-specific, since not many non-Thinkpad users have complained.  I have tried dhclient with two WLAN-cards (one of which at least works fine on an older laptop with Debian) and on several different WLAN networks always with the same results.

As a quick fix I'd like to know how could I change the default DHCP client from dhclient to pump.  I have found no documentation concerning this anywhere.  If I try to apt-get remove dhcp3-client it also has to remove ubuntu-minimal, which is not recommended.

I am running xubuntu Gutsy and had the same problems in Feisty.  dhclient is version isc-dhclient-V3.0.5

---

