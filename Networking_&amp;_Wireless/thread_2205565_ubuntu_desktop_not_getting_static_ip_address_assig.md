---
title: "ubuntu desktop not getting static ip address assigned by DHCP server"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by rhunt2 on 2014-02-14
> All, I have my DHCP server that is set to assign a static IP address to my desktop however my desktop is getting a dynamic IP address
Here is my DHCP.conf


```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#
key "rndc-key" {
        algorithm hmac-md5;
        secret "it's a secret";
};
include "/etc/bind/rndc.key";
#DDNS information
ddns-update-style interim;
ddns-domainname "example.com";
ddns-rev-domainname "in-addr.arpa.";
# Option definitions common to network
option domain-name "example.com";
option domain-name-servers ns.example.com;
option routers 192.168.6.1;
option broadcast-address 192.168.6.255;
default-lease-time 600;
max-lease-time 7200;
# If this DHCP serveris the offical server for the local network
authoritative;
# Logging
log-facility local7;
# This is a very basic subnet declaration.
subnet 192.168.6.0 netmask 255.255.255.0 {
  range 192.168.6.21 192.168.6.200;
        zone example.com. {
                primary 192.168.6.13;
                key "rndc-key";
        }
        zone 6.168.192.in-addr.arpa. {
                primary 192.168.6.13;
                key "rndc-key";
        }
}
host virtualguest0 {
  hardware ethernet 08:00:27:A8:7C:B5;
  fixed-address 192.168.6.5;
}
host virtualguest1 {
  hardware ethernet 08:00:27:4B:58:70;
  fixed-address 192.168.6.6;
}
host virtualguest2 {
  hardware ethernet 08:00:27:6F:31:1A;
  fixed-address 192.168.6.7;
}
host virtualguest3 {
  hardware ethernet 08:00:27:14:B8;F1;
  fixed-address 192.168.6.11;
}
host oryx.pacificcabinets.com {
  hardware ethernet B8:CA:3A:8C:40:52;
  fixed-address 192.168.6.12;
}
host virtualguest4 {
  hardware ethernet 08:00:27:00:37:29;
  fixed-address 192.168.6.13;
}
```

> Here is my desktop wired configuration:
```
Device MAC address: 08:00:27:14:B8:F1 (eth0)
IPv4 settings:
Method Automatic (DHCP)
my connection information shows:
192.168.6.23 
```> (This is in my Dynamic range. What's up)
and I do not want to set it manually I want DHCP to give out my IP's 

---

### Post by rhunt2 on 2014-02-14
(Solved myself) needed to look harder and my typing error in MAC Address ; should have been :

---

