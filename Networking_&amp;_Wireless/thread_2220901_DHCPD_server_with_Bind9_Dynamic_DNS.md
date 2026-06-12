---
title: "DHCPD server with Bind9 Dynamic DNS"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by nethompson on 2014-04-29
I don't quite understand what's going on here. It seems that Bind is trying to update with my nameserver hostname when a client connects:

Office named[10117]: client 192.168.2.20#35215: updating zone 'home.local/IN': update unsuccessful: office.home.local: 'name not in use' prerequisite not satisfied (YXDOMAIN)
Office named[10117]: client 192.168.2.20#54244: updating zone 'home.local/IN': update unsuccessful: office.home.local/TXT: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)
Office dhcpd: Forward map from office.home.local to 192.168.2.6 FAILED: Has an address record but no DHCID, not mine.
Office dhcpd: DHCPREQUEST for 192.168.2.6 from 2c:b4:3a:da:47:43 (Nicks-iPhone) via eth0
Office dhcpd: DHCPACK on 192.168.2.6 to 2c:b4:3a:da:47:43 (Nicks-iPhone) via eth0



The client is obviously not my ns and I can't figure out why it's acting like this. Here are my config files:


named.conf.local
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

include "/etc/bind/rndc.key";
zone "home.local" {
    type master;
    forwarders { 192.168.2.1; };
    file "/var/lib/bind/zones/db.home";
    allow-update { key ddns-key; };
    allow-transfer { 192.168.2.0/24; };
};
zone "2.168.192.home.local" {
    type master;
    forwarders { 192.168.2.1; };
    file "/var/lib/bind/zones/db.2.168.192.in-addr.arpa";
    allow-update { key ddns-key; };
    allow-transfer { 192.168.2.0/24; };
};
zone "1.0.12.home.local" {
    type master;
    forwarders { 12.0.1.1; };
    file "/var/lib/bind/zones/db.1.0.12.in-addr.arpa";
    allow-update { key ddns-key; };
};
acl "trusted" {
    192.168.2.0/24;
    12.0.1.0/24;
    127.0.0.1/32;
};

```


named.conf.options
```

options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

     forwarders {
         192.168.2.1;
        8.8.8.8;
     };
    listen-on { 192.168.2.20;127.0.0.1; };
    allow-query { any; };
    allow-recursion { trusted; };
    allow-query-cache { trusted; };
     max-ncache-ttl 300;

    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //========================================================================
//    dnssec-validation auto;

    auth-nxdomain no;    # conform to RFC1035
//    listen-on-v6 { any; };
};

```

dhcpd.conf
```

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-updates on;
ddns-update-style interim;
ddns-domainname "home.local";
ddns-rev-domainname "in-addr.arpa";
ddns-hostname "office";
allow unknown-clients;
option ntp-servers us.pool.ntp.org;
ignore client-updates;
update-static-leases on;
use-host-decl-names on;
include "/etc/bind/rndc.key";

zone home.local. {
    primary 192.168.2.20;
    key "ddns-key";
}
zone 2.168.192.home.local. {
    primary 192.168.2.20;
    key "ddns-key";
}
zone 1.0.12.home.local. {
    primary 12.0.1.1;
    key "ddns-key";
}

# option definitions common to all supported networks...
option domain-name "home.local";
option domain-name-servers 192.168.2.20,12.0.1.1;

default-lease-time 43200;
max-lease-time 86400;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {0011.204e.ecc0
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
subnet 192.168.2.0 netmask 255.255.255.0 {
  interface eth0;
  range 192.168.2.2 192.168.2.254;
  option domain-name-servers 192.168.2.20;
  option domain-name "home.local";
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;
  default-lease-time 43200;
  max-lease-time 86400;
}

host dns_dhcp {
    hardware ethernet ------;
    fixed-address 192.168.2.20;
}

host office {
    hardware ethernet ------;
    fixed-address 192.168.2.21;
}

host wifi {
    hardware ethernet ------;
    fixed-address 192.168.2.2;
}

host router {
    hardware ethernet ------;
    fixed-address 192.168.2.1;
}

host dvr {
    hardware ethernet ------;
    fixed-address 192.168.2.16;
}

host printer {
    hardware ethernet ------;
    fixed-address 192.168.2.33;
}

host wireless-cam-vm {
    hardware ethernet ------;
    fixed-address 192.168.2.42;
}

host cam1 {
    hardware ethernet ------;
    fixed-address 192.168.2.44;
}

host cam2 {
    hardware ethernet ------;
    fixed-address 192.168.2.50;
}

host switch {
    hardware ethernet ------;
    fixed-address 192.168.2.3;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

```


zone file db.home
```

$TTL 86400    ; 1 day
@    IN SOA    home.local. root.home.local. (
                2013123809 ; serial
                604800     ; refresh (1 week)
                86400      ; retry (1 day)
                2419200    ; expire (4 weeks)
                604800     ; minimum (1 week)
                )
@        IN    NS    office.
office        IN    A    192.168.2.20
office        IN    A    192.168.2.21
cam1        IN    A    192.168.2.44
cam2        IN    A    192.168.2.50
dvr        IN    A    192.168.2.16
localhost    IN    A    127.0.0.1
modem        IN    A    192.168.100.1
router        IN    A    192.168.2.1
wifi        IN    A    192.168.2.2

```


zone file db.2.168.192.in-addr.arpa
```

$TTL 86400    ; 1 day
@        IN SOA    home.local. root.home.local. (
                2013121209 ; serial
                604800     ; refresh (1 week)
                86400      ; retry (1 day)
                2419200    ; expire (4 weeks)
                604800     ; minimum (1 week)
                )
            NS    home.local.    
20            PTR    office.home.local.    
20            PTR    home.local.    
21            PTR    office.home.local.
1            PTR    router.
16            PTR    dvr.
2            PTR    wifi.
44            PTR    cam1.
50            PTR    cam2.

```


zone file db.1.0.12.in-addr.arpa
```

$TTL 1D

@        IN    SOA    office.home.local. root.home.local. (

                                2013121101 ;serial
                                604800     ; refresh (1 week)
                86400      ; retry (1 day)
                2419200    ; expire (4 weeks)
                604800     ; minimum (1 week)
                                )

                IN    NS    home.local.
                IN    A    12.0.1.1
1                IN    PTR    officevpn.
localhost            IN    A    127.0.0.1

```

---

### Post by nethompson on 2014-05-01
Should I assume nobody knows what's going on here?

---

### Post by papibe on 2014-05-01
Hi nethompson.

What is the hostname and IP of the DNS server?
Is DHCPD running on the same machine?

Is it named 'office'?

It looks like 'office' is requesting a lease from DHCPD which it shouldn't be if it is the DHCP/DNS server. 'office' should have an static IP.

Your reverse zone file db.2.168.192.in-addr.arpa has the wrong format. The list of hosts should be like:
```
20    PRT    office.home.local.
44    PRT    cam1.home.local.
16    PTR    dvr.home.local.
...
```    
At first glance it doesn't look like DHCPD is updating DNS. Could you check the name of the key inside the key file is ddns-key?

For instance:
```
$ sudo head -n1 /etc/bind/rndc.key
key "ddns-key" {
```
Regards.

---

### Post by nethompson on 2014-05-02
Whoops! Stupid me! I pasted the wrong zone information for my reverse zone. I've corrected it. Thanks for replying papibe. Yes, office is the host running DHCPD and DNS and I do have it set to static. The syslog output that I pasted is from my iPhone requesting a lease. I agree with what you said about office requesting a lease but it's doing this when I have a client request the lease. It's like it's taking over the hostname that's making the request if that makes any sense...

I checked the key name inside of the key file and it's correct.
```

sudo head -n1 /etc/bind/rndc.key 
key "ddns-key" {

```

---

### Post by papibe on 2014-05-02
Could you post the content of theses file on 'office'?
```
/etc/network/interfaces

/etc/resolv.conf

/etc/nsswitch.conf
```

Also, reverse zones should be called using the 'in-addr.arpa' format (regardless of how the zone file is named):
```
zone "2.168.192.in-addr.arpa" {
    type master;
    ...
};
```
Remember to increase the serial number after a change on the files. For example, from this
```
2013121209 ; serial
```
to:
```
20131212**[COLOR="#FF0000"]10[/COLOR]** ; serial
```
Regards.

---

### Post by nethompson on 2014-05-02
That's interesting to know about the zone file format. I didn't know it was required to be that way, thanks.

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth1 inet static
address 192.168.2.20
netmask 255.255.255.0
gateway 192.168.2.1
dns-domain home.local
dns-nameservers 127.0.0.1,192.168.2.20,192.168.2.1 
dns-search home.local

```

/etc/resolv.conf:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search home.local

```

/etc/nsswitch.conf:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns [NOTFOUND=continue] mdns4_minimal mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

