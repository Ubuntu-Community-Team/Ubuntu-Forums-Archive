---
title: "Can't resolve internet addresses"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by keymoo on 2008-11-09
Hi there,

I have a cable modem connected to my ubuntu 8.04 server with an ethernet cable. The ubuntu server has another NIC connected to a switch, I then have all my home PCs connected to this switch.

Just so we're clear, the path from the home PC to the internet is:

```
Home PC
 |
Netgear switch
 |
Ubuntu Server 8.04
 |
Cable Modem
 |
Internet
```The ubuntu server software stack between the two NICS is:

```
Internal NIC
 |
Shorewall firewall
 |
Squid Proxy
 |
Dansguardian content filter
 |
External NIC (to cable modem)
```The ubuntu server external NIC is set up with DHCP to get an IP address from the cable modem. The ubuntu server internal NIC is a static IP (10.0.0.1). The ubuntu server has dhcpd v 3.0.6 running to serve internet addresses to the home PCs. This all works OK, in the sense that all home PCs get an IP address OK, with the correct subnet mask, default gateway. The ubuntu server external NIC gets an ip address fine from the cable modem.

**Network tests done**

[LIST]
[*]I can ping [www.google.com]("http://www.google.com") from the ubuntu server, no problems.
[*]I cannot ping [www.google.com]("http://www.google.com") from the home PCs
[*]The home PCs can ping the IP address of the internal and external NIC of the ubuntu server fine
[*]ping [www.google.com]("http://www.google.com") from a home PC (WinXP) fails with "Ping request could not find host [www.google.com]("http://www.google.com"). Please check the name and try again."
[*]ping 209.85.129.147 from a home PC fails with "Request timed out"
[*]Browsing to 209.85.129.147 from a home PC works fine and shows the google home page
[*]I tried manually configuring the DNS servers on the home PC Win XP machine to use the opendns.org name servers. Made no difference.
[/LIST]
I'm not sure if my problems are with the DHCP server or with the firewall configuration. My /etc/dhcp3/dhcpd.conf is here:
```
# Home LAN
subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.2 10.0.0.20;
    default-lease-time 86400;
    max-lease-time 86400;
    option routers 10.0.0.1;
    option ip-forwarding off;
    option broadcast-address 10.0.0.255;
    option subnet-mask 255.255.255.0;
    option domain-name-servers 62.2.17.61, 62.2.24.158;
    }

```Shorewall policy file:
```
#
# Shorewall version 3.4 - Sample Policy File for two-interface configuration.
# Copyright (C) 2006 by the Shorewall Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# See the file README.txt for further details.
#------------------------------------------------------------------------------
# For information about entries in this file, type "man shorewall-policy"
#
# See [http://shorewall.net/Documentation.htm#Policy](http://shorewall.net/Documentation.htm#Policy) for additional information.
#
###############################################################################
#SOURCE        DEST        POLICY        LOG LEVEL    LIMIT:BURST

#
# Note about policies and logging:
#    This file contains an explicit policy for every combination of
#    zones defined in this sample.  This is solely for the purpose of
#    providing more specific messages in the logs.  This is not
#    necessary for correct operation of the firewall, but greatly
#    assists in diagnosing problems.
#

#
# Policies for traffic originating from the local LAN (loc)
#
# If you want to force clients to access the Internet via a proxy server
# on your firewall, change the loc to net policy to REJECT info.
loc    net    ACCEPT
loc        $FW        ACCEPT
loc        all        REJECT        info

#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
$FW        net        ACCEPT
$FW        loc        ACCEPT        info
$FW        all        ACCEPT        info

#
# Policies for traffic originating from the Internet zone (net)
#
net        $FW        DROP        info
net        loc        DROP        info
net        all        DROP        info

# THE FOLLOWING POLICY MUST BE LAST
all        all        REJECT        info


#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
```The shorewall rules file:
```
#
# Shorewall version 3.4 - Sample Rules File for two-interface configuration.
# Copyright (C) 2006 by the Shorewall Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# See the file README.txt for further details.
#------------------------------------------------------------------------------
# For information about entries in this file, type "man shorewall-rules"
#
# For more information, see http://www.shorewall.net/Documentation.htm#Rules
#
#############################################################################################################
#ACTION        SOURCE        DEST        PROTO    DEST    SOURCE        ORIGINAL    RATE        USER/
#                            PORT    PORT(S)        DEST        LIMIT        GROUP
#                                PORT    PORT(S) DEST            LIMIT    GROUP
#
#    Accept DNS connections from the firewall to the network
#
DNS/ACCEPT    $FW        net
#
#    Accept SSH connections from the local network for administration
#
SSH/ACCEPT    loc        $FW
#
#    Allow Ping from the local network
#
REDIRECT    loc    8080    tcp    www    -    !10.0.0.1

# 
# Allow bit torrents to 41169
#
Ping/ACCEPT    loc        $FW

#
# Reject Ping from the "bad" net zone.. and prevent your log from being flooded..
#

Ping/ACCEPT    loc    net

DNAT        net        loc:10.0.0.3:41669        tcp        41669
#

Ping/REJECT    net        $FW
ACCEPT        $FW        loc        icmp
# ACCEPT    net    loc    all
ACCEPT    $FW    net    tcp
ACCEPT    $FW    net    icmp

#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

```
I'd appreciate very much any ideas on further troubleshooting.

---

### Post by Iowan on 2008-11-09
You might try disabling the firewall (and/or proxy) to see if problem goes away.  Verify what **option ip-forwarding off;** does - my server doesn't have that line.  Also, I'm not sure having the **option routers 10.0.0.1;** line pointing to the internal IP address will work (although it seems to work from the server??).

---

### Post by htmlland on 2008-11-09
Hey! I have the exact same set up as you have and ive only just got it all working :), have you got a DNS server setup on the server? If not that could help so all in the internal traffic uses that as its DNS/gateway server and then the server will ue the open dns servers for its requests.

Michael

---

