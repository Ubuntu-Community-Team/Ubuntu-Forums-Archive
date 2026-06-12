---
title: "wrtg54g setup problem"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by cary_m on 2007-11-14
I am attempting to set up a linksys wireless router for my home
network.

My specs
  Linksys wrt54G version 4 wireless router
  Motorola Surfboard sb4220 cable modem
  Ubuntu Linux laptop
  eMac desktop
  Comcast isp
  DHCP

For years I have been using the surfboard.  I can plug in either of my
two computers and it works fine.  I simply turn on the surfboard and
then the computer and get an address via DHCP.
The surfboard has IP address 192.168.100.1 visible to my browser.
No problem.

Working configuration
  cable - surfboard - laptop

Desired configuration
  cable - surfboard - linksys - laptop



When I insert the linksys between surfboard and laptop everything
beyond the linksys disappears.  First I tried leaving all the default
settings on the linksys.
Browsing to the set up page at 192.168.1.1 I have the following
settings.


  Internet connection type: Automatic configuration - DHCP
  Router Name:  WRT54G
  MTU: Auto
  Size: 1500

  Router local IP: 192.168.1.1
  Subnet Mask:     255.255.255.0

  DHCP Server: enabled
  etc.

I tried changing the router local IP to 192.168.100.2
But even before dealing with that issue there is another problem.  The
settings do not get assigned.  When I browse from the "Setup" page to
the "Status" page I see this:

  Login Type:       Automatic Configuration - DHCP
  IP Address:       0.0.0.0
  Subnet Mask:      0.0.0.0
  Default Gateway:  0.0.0.0

I had expected this:

  Login Type:       Automatic Configuration - DHCP
  IP Address:       192.168.100.2
  Subnet Mask:      255.255.255.0
  Default Gateway:  192.168.100.1



The routing table for the linksys:
Destination LAN     Subnet Mask     Gateway     Interface
 192.168.100.0     255.255.255.0    0.0.0.0   LAN & Wireless


The routing table for the laptop:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   *               255.255.255.0   U     0      0        0 eth1
default         192.168.100.1   0.0.0.0         UG    0      0        0 eth1


The routing table for the laptop + surfboard:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
24.9.72.0       *               255.255.248.0   U     0      0        0 eth1
default         c-nn-n-nn-n.hsd 0.0.0.0         UG    0      0        0 eth1




What am I missing here?

---

### Post by Unconscious on 2007-11-14
The settings under the WRT54G status are all 0's because you're not connected.

Not familiar with the surfboard, but it sounds like it's acting as something more than just a cable/dsl modem. It's probably doing some routing.

It seems as if you are not understanding the duality of the situation your WRT54G is in. The network from the WRT54G out is referred to as the WAN (Wide Area Network).

From the WRT54G in it called the LAN (Local Area Network).

The gateway it is supposed to connect through is the surfboard, it has an address of 192.168.100.1, if I remember correctly (can't see your post while writing this reply). That is the WAN address at the interface of your WRT54G. The LAN address is 192.168.1.1. I wouldn't recommend messing with that, at least until you have a much clearer idea about what you are doing.

If you can browse to the router, then everything on the LAN side of your routed network is ok.

Before you can get anywhere you are going to have to configure the WRT54G so that it can connect to the surfboard. The WRT54G has a number of different connection modes one of which should be static IP. Use that, and give it the surfboard's IP as the WAN address.


Good luck.

---

