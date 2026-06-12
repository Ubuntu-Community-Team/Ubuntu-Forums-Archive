---
title: "LTSP with different DHCP"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by theller on 2011-05-04
I set up a server (9.10) and have thin and fat clients working off it. The problem is if I connect it to the schools network it will conflict with the other server handing out IP's (192.168.1.1) 

Right now the server has 2 cards one connected to the network with a fixed ip and the other card goes to a router connected to the clients. Here is my dhcp config

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.1 192.168.0.254;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

Any help would be appreciated.

---

### Post by theller on 2011-05-05
Okay... how about this...can I assign ip address that the other server is not going to use?

---

