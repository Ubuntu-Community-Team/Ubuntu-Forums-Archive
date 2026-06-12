---
title: "DHCP won't start"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by 3rdtechie on 2008-01-02
Help, my server has fallen and can’t get up. I can’t get my LTSP thin client server to connect with the client. :confused:

I’ve narrowed it down to the DHCP server. I have 2 network cards: Eth0 for the internet gateway, and Eth1 for the LTPS network. Both run through Linksys routers.

Here is what the DHCP.config file says:
> 
    default-lease-time 600;
    max-lease-time 7200;

    # LTSP Think client Network
    subnet 192.168.0.5 netmask 255.255.255.0 {
    range 192.168.0.100 192.168.0.150;
    INTERFACES=”eth1&#8243;
    auto eth1
    iface eth1 inet 192.168.1.251
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.254;
    # next-server 192.168.0.253;
    option subnet-mask 255.255.255.0;
    option root-path “/opt/ltsp/i386&#8243;;
    if substring( option vendor-class-identifier , 0 , 9 ) = “PXEClient” {
    filename “/ltsp/i386/pxelinux.0&#8243;;
    }
    else {
    filename “/ltsp/i386/nbi.img”;
    }
    if substring( option vendor-class-identifier , 0 , 9 ) = “Etherboot” {
    filename “/ltsp/i386/vmlinuz.etherboot”;
    }
    else {
    filename “/ltsp/i386/nbi.img”;
    }
    }
    # Thin Client LTSP Network
    subnet 192.168.0.10 netmask 255.255.255.2 {
    authoritative;
    INTERFACES=”eth0&#8243;
    auto eth0
    iface eth0
    option routers 192.168.0.252;
    range 192.168.1.201 192.168.1.300;
    pool {
    range 192.168.1.151 192.168.1.200;
    allow 00:60:97:DF:C0:13;
    }
    }

When I try to start the DHCP server, I get a “Failed command Execution” error.  My syslog  looks like this:

> Jan  2 21:57:23 daddy-server dhcpd: Internet Systems Consortium DHCP Server V3.0.5
Jan  2 21:57:23 daddy-server dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Jan  2 21:57:23 daddy-server dhcpd: All rights reserved.
Jan  2 21:57:23 daddy-server dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  2 21:57:23 daddy-server dhcpd: Wrote 0 leases to leases file.
Jan  2 21:57:23 daddy-server dhcpd:
Jan  2 21:57:23 daddy-server dhcpd: No subnet declaration for eth1 (192.168.1.251).
Jan  2 21:57:23 daddy-server dhcpd: ** Ignoring requests on eth1.  If this is not what
Jan  2 21:57:23 daddy-server dhcpd:    you want, please write a subnet declaration
Jan  2 21:57:23 daddy-server dhcpd:    in your dhcpd.conf file for the network segment
Jan  2 21:57:23 daddy-server dhcpd:    to which interface eth1 is attached. **
Jan  2 21:57:23 daddy-server dhcpd:
Jan  2 21:57:23 daddy-server dhcpd:
Jan  2 21:57:23 daddy-server dhcpd: Not configured to listen on any interfaces!

Why won’t it work?  How do I fix it?  Where can I go for help?  Help!

---

### Post by bwtranch on 2008-01-02
I do believe this is your problem:

an 2 21:57:23 daddy-server dhcpd: No subnet declaration for eth1 (192.168.1.251).
Jan 2 21:57:23 daddy-server dhcpd: ** Ignoring requests on eth1. If this is not what
Jan 2 21:57:23 daddy-server dhcpd: you want, please write a subnet declaration
Jan 2 21:57:23 daddy-server dhcpd: in your dhcpd.conf file for the network segment
Jan 2 21:57:23 daddy-server dhcpd: to which interface eth1 is attached. **
Jan 2 21:57:23 daddy-server dhcpd:
Jan 2 21:57:23 daddy-server dhcpd:
Jan 2 21:57:23 daddy-server dhcpd: Not configured to listen on any interfaces!

Please look at the link above this to configure your system.

---

### Post by 3rdtechie on 2008-01-05
I used GDHCPD, a GUI frontend to DHCP3 to help with some of my problems.  I still have one though.  I am getting this error

> Internet Systems Consortium DHCP Server V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

/etc/dhcp3/dhcpd.conf line 86: semicolon expected.
default-lease-time 
^
Configuration file errors encountered -- exiting

Here is my DHCP3.Config file
> 
ddns-update-style none;
ddns-updates off;
allow client-updates;
one-lease-per-client true;
allow bootp;
option T150 code 150 = string;
authoritative;
default-lease-time 600;
max-lease-time 7200;

# LTSP Thin client Network
subnet 192.168.0.0 netmask 255.255.255.0 {
    interface eth1;
    max-lease-time 7200;
    option domain-name "LTSP.Edubuntu.com";
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.10;
}

Is this a bug, or can this be fixed?

---

### Post by 3rdtechie on 2008-01-05
I got it! Thanks! :)

---

### Post by HermanAB on 2008-01-05
The problem is in the previous line.  Comment the previous line out, since it is probably wrong/deprecated/unnecessary.

Cheers,

Herman

---

