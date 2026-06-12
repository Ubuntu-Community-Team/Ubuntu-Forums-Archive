---
title: "DDNS using BIND9 and DHCPD3"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by bstempi on 2007-02-08
Hi all!

I've been doing a lot of reading lately about how to set up Dynamic DNS using DHCPD3 to update the DNS server.  I figured that the first part of doing this would be a correcly configured DHCP server.  Below is my dhcpd.conf file:

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.4.2.2 2002/07/10 03:50:33 peloy Exp $
#
#  authorative;
#  server-identifier gateway;

# option definitions common to all supported networks...
option domain-name "bstempi.servebeer.com";
option domain-name-servers 192.168.0.1;

# options inserted for Dynamic DNS
#  ddns-domainname "bstempi.servebeer.com.";
# ddns-update-style interim;
# ddns-updates on;

option subnet-mask 255.255.255.0;
default-lease-time 600;
max-lease-time 900;
subnet 192.168.0.0 netmask 255.255.255.0 {
   range 192.168.0.5 192.168.0.254;
   option broadcast-address 192.168.0.255;
   option routers 192.168.0.1;
}

host fileserver01 {
    hardware ethernet 00:14:6c:76:74:c2;
    fixed-address 192.168.0.3;
}

host webserver01 {
    hardware ethernet 00:02:e3:24:2b:04;
    fixed-address 192.168.0.4;
}

```

Some of the documentation I've read claimed that adding the autorative statement along with the ddns-<insertddnsstuffhere> statements were required.  Anytime I uncomment the authorative or ddns-* lines, dhcpd blows up and spits out the following to the syslog:
```

Feb  8 23:15:02 firewall01 dhcpd: /etc/dhcpd.conf line 6: expecting a parameter or declaration.
Feb  8 23:15:02 firewall01 dhcpd:   authorative;
Feb  8 23:15:02 firewall01 dhcpd:   ^
Feb  8 23:15:02 firewall01 dhcpd: /etc/dhcpd.conf line 14: expecting a parameter or declaration.
Feb  8 23:15:02 firewall01 dhcpd:  ddns-domainname
Feb  8 23:15:02 firewall01 dhcpd:  ^
Feb  8 23:15:02 firewall01 dhcpd: /etc/dhcpd.conf line 15: expecting a parameter or declaration.
Feb  8 23:15:02 firewall01 dhcpd:  ddns-update-style
Feb  8 23:15:02 firewall01 dhcpd:  ^
Feb  8 23:15:02 firewall01 dhcpd: /etc/dhcpd.conf line 16: expecting a parameter or declaration.
Feb  8 23:15:02 firewall01 dhcpd:  ddns-updates
Feb  8 23:15:02 firewall01 dhcpd:  ^
Feb  8 23:15:02 firewall01 dhcpd: Configuration file errors encountered -- exiting
Feb  8 23:15:02 firewall01 dhcpd: exiting.

```

Does anybody have any clue as to what's causing this?  Any help is greatly appreciated.

TIA,
     Brian

---

### Post by ChristopherDante on 2007-06-06
you have to uncomment the line

 ddns-update-style interim;

see also 

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-dhcp-configuring-server.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-dhcp-configuring-server.html)

hope this helps...

---

### Post by hanasaki on 2007-12-27
would you share your bind9 config please?

---

### Post by bstempi on 2007-12-27
Sorry for not closing this thread...

Unknown to me, the packages I had were wrong.  For DNS, I installed BIND instead of BIND9.  I incorrectly assumed that they were the same thing.  Likewise for DHCP, I installed DHCP-Server instead of DHCP3-Server.  After discovering that and fixing my packages, my error messages went away.  My testing afterwards was limited, so I don't know if my config file works 100%.

Thanks to all who replied!

---

