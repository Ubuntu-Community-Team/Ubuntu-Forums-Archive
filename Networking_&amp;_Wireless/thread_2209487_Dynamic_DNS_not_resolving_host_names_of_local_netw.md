---
title: "Dynamic DNS not resolving host names of local network machines"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by dispair1981 on 2014-03-05
I have recently installed ubuntu 13.10 server on an "OEM Production 2550L2D-MxPC Intel NM10 2 x 204Pin Intel GMA 3650 Black Mini / Booksize Barebone System - OEM " with 8GB of RAM and a 1TB HDD.  during the install I installed SSH and DNS from the selection menu.  After the install I installed isc-dhcp-server, squid, and webmin.

I am trying to setup a web filter/gateway, I want to test each section of the device as it is setup because I have had some problems with applications not being able to get through the gateway on test machines.  Currently I am trying to get DNS resolution working and while I have setup DHCP with the key for DNS and have no errors stopping the daemons from loading, I am unable to resolve host names of local machines.

I have tried pinging the gateway (named Cerberus) from a windows machine and an android tablet.

I am able to ping the machine with IP 192.168.1.10
I am able to ping the machine with domain name keystoneaquaria.com (setup on local DNS)
I am able to ping windows machines with hostnames (angels-HP, Randy-HP, Robbie-HP, angel-hp)
I am able to ping Ubuntu machines (Media-1, Cerberus, Kerberus) with respective IP's 192.168.1.25, 192.168.1.10, 192.168.1.11
I am unable to ping Ubuntu machines with hostnames Media-1, Cerberus, Kerberus

Does anyone know how to resolve this issue of not being able to resolve Ubuntu hostnames on local network with local DNS (Bind9), and Ubuntu DHCP (isc-dhcp-server)?

I have included my config files for Bind9, isc-dhcp-server below!

/etc/bind/named.conf
```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```
/etc/bind/named.conf.options
```

options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    // forwarders {
    //     0.0.0.0;
    // };

    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
    //========================================================================
    dnssec-validation auto;

    auth-nxdomain no;    # conform to RFC1035
    forwarders {
        192.168.1.1;
    };
    listen-on-v6 { any; };
};


```
/etc/bind/named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
key "rndc-key" {
    algorithm hmac-md5;
    secret "qFsmFzirhBcSMWs1+sV3wg==";
};

zone "keystoneaquaria.com" {
    type master;
    file "/etc/bind/db.keystoneaquaria.com";
};

```
/etc/bind/db.keystoneaquaria.com
```

;
; BIND data file for keystoneaquaria
;
$TTL    604800
@    IN    SOA    keystoneaquaria.com. root.keystoneaquaria.com. (
            4
            604800
            86400
            2419200
            604800 )
;
@    IN    NS    keystoneaquaria.com.
@    IN    A    192.168.1.10
@    IN    AAAA    ::1
ns    IN    A    192.168.1.10
Cerberus.    IN    A    192.168.1.10

```

/etc/bind/db.192
```

;
; BIND reverse data file for 192.168.1 interface
;
$TTL    604800
@    IN    SOA    ns.keystoneaquaria.com.    root.keystoneaquaria.com. (
                  1        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.
1    IN    PTR    ns.keystoneaquaria.com.
2    IN    PTR    ibr.keystoneaquaria.com.


```
/etc/dhcp/dhcpd.conf
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
ddns-update-style interim;
update-static-leases on;

key "rndc-key" {
    algorithm hmac-md5;
    secret "qFsmFzirhBcSMWs1+sV3wg==";
};

allow unknown-clients;
use-host-decl-names on;

#building DNS Zones
zone    keystoneaquaria.com. {
    primary localhost;
    key rndc-key;
}
zone 1.168.192.in-addr.arpa. {
    primary localhost;
    key rndc-key;
}

# option definitions common to all supported networks...
option domain-name "keystoneaquaria.com";
option domain-name-servers 192.168.1.10, 192.168.2.1, 192.168.1.1;

default-lease-time 600;
max-lease-time 800;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
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
subnet 192.168.1.0 netmask 255.255.255.0 {
    ddns-updates on;
    range 192.168.1.20 192.168.1.50;
    option domain-name-servers 192.168.1.10;
    option domain-name "keystoneaquaria.com";
    option routers 192.168.1.1;
    # option netbios-node-type 2;
    ddns-domainname "keystoneaquaria.com";
    ddns-rev-domainname "in-addr.arpa.";
    max-lease-time 800;
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

/etc/dhcp/dhclient.conf
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

#send host-name "andare.fugue.com";
send host-name = gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers,
    dhcp6.domain-search, dhcp6.fqdn,
    dhcp6.name-servers, dhcp6.sntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by papibe on 2014-03-05
Hi dispair1981.

I'm running both bind and isc-dhcp-server on my home server.

It looks like isc-dhcp-server, is not updating the leases into bind. Note that your file /etc/bind/db.keystoneaquaria.com has not been updated with the current leases.

Look into your /var/log/syslog for entries like:
```
Mar  5 21:05:34 youserver named[984]: client 192.168.1.1#45057: signer "rndc-key" approved
```
to check if the key is being accepted, and for entries like this:
```
Mar  5 21:05:34 yourserver named[984]: client 192.168.1.1#59899: updating zone 'yourdomain/IN': adding an RR at 'aclient.yourdomain' A
Mar  5 21:05:34 yourserver named[984]: client 192.168.1.1#59899: updating zone 'yourdomain/IN': adding an RR at 'aclient.yourdomain' TXT
```
to check for updates from isc-dhcp-server to bind.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by dispair1981 on 2014-03-06
I checked the syslog and did not find any of the lines you mention, I did however find these lines:
```

Mar  6 00:33:10 Cerberus named[1285]:   validating @0x7f8bf0040910: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:10 Cerberus named[1285]: error (no valid RRSIG) resolving 'kifreegames.com/DS/IN': 192.168.1.1#53
Mar  6 00:33:11 Cerberus named[1285]:   validating @0x7f8bf8031310: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:11 Cerberus named[1285]: error (no valid RRSIG) resolving 'freekigames.com/DS/IN': 192.168.1.1#53
Mar  6 00:33:15 Cerberus named[1285]: client 127.0.0.1#47179: update 'keystoneaquaria.com/IN' denied
Mar  6 00:33:15 Cerberus dhcpd: DHCPREQUEST for 192.168.1.31 from 40:f0:2f:43:48:32 (Angels-hp) via p2p1
Mar  6 00:33:15 Cerberus dhcpd: DHCPACK on 192.168.1.31 to 40:f0:2f:43:48:32 (Angels-hp) via p2p1
Mar  6 00:33:15 Cerberus dhcpd: Unable to add forward map from Angels-hp.keystoneaquaria.com to 192.168.1.31: REFUSED
Mar  6 00:33:26 Cerberus named[1285]: client 127.0.0.1#47179: update 'keystoneaquaria.com/IN' denied
Mar  6 00:33:27 Cerberus dhcpd: DHCPREQUEST for 192.168.1.20 from 50:f5:20:b7:39:05 via p2p1
Mar  6 00:33:27 Cerberus dhcpd: DHCPACK on 192.168.1.20 to 50:f5:20:b7:39:05 (android-1337258ba1171c83) via p2p1
Mar  6 00:33:27 Cerberus dhcpd: Unable to add forward map from android-1337258ba1171c83.keystoneaquaria.com to 192.168.1.20: REFUSED
Mar  6 00:33:32 Cerberus named[1285]:   validating @0x7f8bf8031310: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:32 Cerberus named[1285]: error (no valid RRSIG) resolving 'googleadservices.com/DS/IN': 192.168.1.1#53
Mar  6 00:33:36 Cerberus named[1285]:   validating @0x7f8c004cfdb0: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:36 Cerberus named[1285]: error (no valid RRSIG) resolving 'chartboost.com/DS/IN': 192.168.1.1#53
Mar  6 00:33:37 Cerberus named[1285]:   validating @0x7f8c004cfdb0: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:37 Cerberus named[1285]: error (no valid RRSIG) resolving 'mobage.com/DS/IN': 192.168.1.1#53
Mar  6 00:33:37 Cerberus named[1285]:   validating @0x7f8bf003e8f0: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:37 Cerberus named[1285]: error (no valid RRSIG) resolving 'ngmoco.com/DS/IN': 192.168.1.1#53
Mar  6 00:33:38 Cerberus named[1285]:   validating @0x7f8bfc04bd70: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:38 Cerberus named[1285]: error (no valid RRSIG) resolving 'crittercism.com/DS/IN': 192.168.1.1#53
Mar  6 00:33:38 Cerberus named[1285]: error (network unreachable) resolving 'crittercism.com/DS/IN': 2001:503:a83e::2:30#53
Mar  6 00:33:39 Cerberus named[1285]:   validating @0x7f8bf003e8f0: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:39 Cerberus named[1285]: error (no valid RRSIG) resolving 'runawayplay.com/DS/IN': 192.168.1.1#53
Mar  6 00:33:39 Cerberus named[1285]: error (network unreachable) resolving 'runawayplay.com/DS/IN': 2001:503:231d::2:30#53
Mar  6 00:33:45 Cerberus named[1285]:   validating @0x7f8bfc04bd70: com SOA: got insecure response; parent indicates it should be secure
Mar  6 00:33:45 Cerberus named[1285]: error (no valid RRSIG) resolving 'game-insight.com/DS/IN': 192.168.1.1#53
```

---

### Post by papibe on 2014-03-06
Add this line to your named.conf.local so it looks something like this:
```
key "rndc-key" {
    algorithm hmac-md5;
    secret "qFsmFzirhBcSMWs1+sV3wg==";
};

[B]controls {
  inet 127.0.0.1 allow { localhost; 192.168.1.10; } keys { "rndc-key"; };
};[/B]

zone "keystoneaquaria.com" {
    type master;
    file "/etc/bind/db.keystoneaquaria.com";
[B]    allow-update { key "rndc-key"; };
    notify yes;[/B]
};

zone "1.168.192.in-addr.arpa" {
  type master;
  file "/etc/bind/db.192";
[B]  allow-update { key "rndc-key"; };
  notify yes;[/B]
};

```
Restart both dhcp-server and bind on the server. On the client, restart the network so that it asks for a new ip:
```
sudo service network-manager restart
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by dispair1981 on 2014-03-06
I have implemented the changed you mentioned, however, the Dynamic DNS is still not functional, If from my gateway I ping Media-1 I get a respose from my ISP DNS search assistant (199.101.28.20)  obviously this is incorrect as Media-1 is (192.168.1.25) and is also DHCP assigned.  If from a windows machine I ping Media-1 or Cerberus I get no response.

Any other suggestions?

/var/log/syslog
```

Mar  6 14:57:00 Cerberus dhcpd: DHCPREQUEST for 192.168.1.22 from 20:16:d8:34:4d:9f (Randy-HP) via p2p1
Mar  6 14:57:00 Cerberus dhcpd: DHCPACK on 192.168.1.22 to 20:16:d8:34:4d:9f (Randy-HP) via p2p1
Mar  6 14:57:00 Cerberus dhcpd: Unable to add forward map from Randy-HP.keystoneaquaria.com. to 192.168.1.22: SERVFAIL
Mar  6 14:57:26 Cerberus named[1313]: client 127.0.0.1#21131: signer "rndc-key" approved
Mar  6 14:57:26 Cerberus named[1313]: client 127.0.0.1#21131: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-67da949a731da1b0.keystoneaquaria.com' A
Mar  6 14:57:26 Cerberus named[1313]: client 127.0.0.1#21131: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-67da949a731da1b0.keystoneaquaria.com' TXT
Mar  6 14:57:26 Cerberus named[1313]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
Mar  6 14:57:26 Cerberus named[1313]: client 127.0.0.1#21131: updating zone 'keystoneaquaria.com/IN': error: journal open failed: unexpected error
Mar  6 14:57:26 Cerberus kernel: [  167.097017] type=1400 audit(1394135846.372:12): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/db.keystoneaquaria.com.jnl" pid=1317 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104
Mar  6 14:57:26 Cerberus dhcpd: DHCPREQUEST for 192.168.1.21 from 34:23:ba:0d:49:37 (android-67da949a731da1b0) via p2p1
Mar  6 14:57:26 Cerberus dhcpd: DHCPACK on 192.168.1.21 to 34:23:ba:0d:49:37 (android-67da949a731da1b0) via p2p1
Mar  6 14:57:26 Cerberus dhcpd: Unable to add forward map from android-67da949a731da1b0.keystoneaquaria.com. to 192.168.1.21: SERVFAIL

```
updated config files.

/etc/bind/named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
key "rndc-key" {
    algorithm hmac-md5;
    secret "qFsmFzirhBcSMWs1+sV3wg==";
};

controls {
    inet 127.0.0.1 allow { 
        localhost; 
        192.168.1.10; 
    }; 
};
zone "keystoneaquaria.com" {
    type master;
    file "/etc/bind/db.keystoneaquaria.com";
    allow-update { key "rndc-key"; };
    notify yes;
};

zone "1.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.192";
    allow-update { key "rndc-key"; };
    notify yes;
};
```

/etc/bind/named.conf.options
```

options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    // forwarders {
    //     0.0.0.0;
    // };

    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
    //========================================================================
    dnssec-enable no;
    dnssec-validation no;

    auth-nxdomain no;    # conform to RFC1035
    forwarders {
        192.168.1.1;
    };
    listen-on-v6 { any; };
};

```
/etc/dhcp/dhcpd.conf
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
ddns-update-style interim;
update-static-leases on;

key "rndc-key" {
    algorithm hmac-md5;
    secret "qFsmFzirhBcSMWs1+sV3wg==";
};

allow unknown-clients;
use-host-decl-names on;

#building DNS Zones

zone    keystoneaquaria.com. {
    primary localhost;
    key rndc-key;
}
zone 1.168.192.in-addr.arpa. {
    primary localhost;
    key rndc-key;
}

# option definitions common to all supported networks...
option domain-name "keystoneaquaria.com";
option domain-name-servers 192.168.1.10;

default-lease-time 600;
max-lease-time 800;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
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
subnet 192.168.1.0 netmask 255.255.255.0 {
    ddns-updates on;
    ddns-update-style interim;
        use-host-decl-names on;
    ddns-domainname "keystoneaquaria.com.";
    ddns-rev-domainname "in-addr.arpa.";
    range 192.168.1.20 192.168.1.50;
    option domain-name-servers 192.168.1.10;
    option domain-name "keystoneaquaria.com";
    option routers 192.168.1.1;
    # option netbios-node-type 2;
    max-lease-time 800;
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

---

### Post by papibe on 2014-03-06
There's improvement:

The key is being recognized now:
```
Mar 6 14:57:26 Cerberus named[1313]: client 127.0.0.1#21131: signer "rndc-key" approved
```
And a successful update is received from dhcpd:
```
Mar 6 14:57:26 Cerberus named[1313]: client 127.0.0.1#21131: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-67da949a731da1b0.keystoneaquaria.com' A
Mar 6 14:57:26 Cerberus named[1313]: client 127.0.0.1#21131: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-67da949a731da1b0.keystoneaquaria.com' TXT
```
However, bind can't write the update to its files:
```
Mar 6 14:57:26 Cerberus named[1313]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
```
I believe it is a permission problem. 'bind' runs as the user 'bind', so it needs read and write permission to the working directory.

Could you post the results of this command:
```
ls -ld /var/cache/bind /etc/bind
```
In my case, those files live in /var/lib/bind, and bind has access to it:
```
$ ls -ld /var/lib/bind/
drwx**[COLOR="#FF0000"]rwx[/COLOR]**r-x 2 root **[COLOR="#FF0000"]bind[/COLOR]** 4096 2014-03-06 07:24 /var/lib/bind/

```
Let us know if that helped you.
Regards.

---

### Post by dispair1981 on 2014-03-06
I changed the perms of /etc/bind, I even, while trying to get it to write, changed all permissions to 777.  When that didn't work I changed them back to the original.  I didn't know about the second folder so I haven't changed any of those.  

The output of the ls command:
```
drwxrwsr-x 2 bind bind 4096 Mar  6 14:49 /etc/bind
drwxrwxr-x 2 root bind 4096 Mar  6 14:54 /var/cache/bind

```
I will check the permissions in the /var/cache/bind folder

Thank you

---

### Post by dispair1981 on 2014-03-06
I chown bind:bind on /var/cache/bind, the owner and group are already bind for /etc/bind, however, when i reboot the machine i still get the same error.  The complete syslog, after reboot, is below, also ls -l for the two directories.

/var/log/syslog

```
Mar  6 20:51:18 Cerberus named[1325]: client 127.0.0.1#43437: signer "rndc-key" approved
Mar  6 20:51:18 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'Media-1.keystoneaquaria.com' A
Mar  6 20:51:18 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'Media-1.keystoneaquaria.com' TXT
Mar  6 20:51:18 Cerberus named[1325]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
Mar  6 20:51:18 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': error: journal open failed: unexpected error
Mar  6 20:51:18 Cerberus kernel: [  420.924161] type=1400 audit(1394157078.009:19): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/db.keystoneaquaria.com.jnl" pid=1328 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104
Mar  6 20:51:18 Cerberus dhcpd: DHCPREQUEST for 192.168.1.25 from 74:d0:2b:3c:f4:43 (Media-1) via p2p1
Mar  6 20:51:18 Cerberus dhcpd: DHCPACK on 192.168.1.25 to 74:d0:2b:3c:f4:43 (Media-1) via p2p1
Mar  6 20:51:18 Cerberus dhcpd: Unable to add forward map from Media-1.keystoneaquaria.com. to 192.168.1.25: SERVFAIL
Mar  6 20:51:19 Cerberus named[1325]: client 127.0.0.1#43437: signer "rndc-key" approved
Mar  6 20:51:19 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-f3838621a6e7b6bc.keystoneaquaria.com' A
Mar  6 20:51:19 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-f3838621a6e7b6bc.keystoneaquaria.com' TXT
Mar  6 20:51:19 Cerberus named[1325]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
Mar  6 20:51:19 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': error: journal open failed: unexpected error
Mar  6 20:51:19 Cerberus kernel: [  422.585122] type=1400 audit(1394157079.673:20): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/db.keystoneaquaria.com.jnl" pid=1326 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104
Mar  6 20:51:19 Cerberus dhcpd: DHCPREQUEST for 192.168.1.28 from 34:23:ba:11:26:b8 (android-f3838621a6e7b6bc) via p2p1
Mar  6 20:51:19 Cerberus dhcpd: DHCPACK on 192.168.1.28 to 34:23:ba:11:26:b8 (android-f3838621a6e7b6bc) via p2p1
Mar  6 20:51:19 Cerberus dhcpd: Unable to add forward map from android-f3838621a6e7b6bc.keystoneaquaria.com. to 192.168.1.28: SERVFAIL
Mar  6 20:51:26 Cerberus named[1325]: client 127.0.0.1#43437: signer "rndc-key" approved
Mar  6 20:51:26 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-16bdde0788822bd7.keystoneaquaria.com' A
Mar  6 20:51:26 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-16bdde0788822bd7.keystoneaquaria.com' TXT
Mar  6 20:51:26 Cerberus named[1325]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
Mar  6 20:51:26 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': error: journal open failed: unexpected error
Mar  6 20:51:26 Cerberus kernel: [  429.118170] type=1400 audit(1394157086.217:21): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/db.keystoneaquaria.com.jnl" pid=1328 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104
Mar  6 20:51:26 Cerberus dhcpd: DHCPREQUEST for 192.168.1.24 from e4:40:e2:21:c1:2e (android-16bdde0788822bd7) via p2p1
Mar  6 20:51:26 Cerberus dhcpd: DHCPACK on 192.168.1.24 to e4:40:e2:21:c1:2e (android-16bdde0788822bd7) via p2p1
Mar  6 20:51:26 Cerberus dhcpd: Unable to add forward map from android-16bdde0788822bd7.keystoneaquaria.com. to 192.168.1.24: SERVFAIL
Mar  6 20:51:29 Cerberus named[1325]: client 127.0.0.1#43437: signer "rndc-key" approved
Mar  6 20:51:29 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'Angels-hp.keystoneaquaria.com' A
Mar  6 20:51:29 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'Angels-hp.keystoneaquaria.com' TXT
Mar  6 20:51:29 Cerberus named[1325]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
Mar  6 20:51:29 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': error: journal open failed: unexpected error
Mar  6 20:51:29 Cerberus kernel: [  432.838430] type=1400 audit(1394157089.945:22): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/db.keystoneaquaria.com.jnl" pid=1326 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104
Mar  6 20:51:30 Cerberus dhcpd: DHCPREQUEST for 192.168.1.31 from 40:f0:2f:43:48:32 (Angels-hp) via p2p1
Mar  6 20:51:30 Cerberus dhcpd: DHCPACK on 192.168.1.31 to 40:f0:2f:43:48:32 (Angels-hp) via p2p1
Mar  6 20:51:30 Cerberus dhcpd: Unable to add forward map from Angels-hp.keystoneaquaria.com. to 192.168.1.31: SERVFAIL
Mar  6 20:51:32 Cerberus named[1325]: client 127.0.0.1#43437: signer "rndc-key" approved
Mar  6 20:51:32 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-67da949a731da1b0.keystoneaquaria.com' A
Mar  6 20:51:32 Cerberus kernel: [  435.049853] type=1400 audit(1394157092.157:23): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/db.keystoneaquaria.com.jnl" pid=1326 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104
Mar  6 20:51:32 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'android-67da949a731da1b0.keystoneaquaria.com' TXT
Mar  6 20:51:32 Cerberus named[1325]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
Mar  6 20:51:32 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': error: journal open failed: unexpected error
Mar  6 20:51:32 Cerberus dhcpd: DHCPREQUEST for 192.168.1.21 from 34:23:ba:0d:49:37 (android-67da949a731da1b0) via p2p1
Mar  6 20:51:32 Cerberus dhcpd: DHCPACK on 192.168.1.21 to 34:23:ba:0d:49:37 (android-67da949a731da1b0) via p2p1
Mar  6 20:51:32 Cerberus dhcpd: Unable to add forward map from android-67da949a731da1b0.keystoneaquaria.com. to 192.168.1.21: SERVFAIL
Mar  6 20:51:36 Cerberus named[1325]: error (network unreachable) resolving 'media-1/A/IN': 2001:500:2f::f#53
Mar  6 20:51:53 Cerberus named[1325]: client 127.0.0.1#43437: signer "rndc-key" approved
Mar  6 20:51:53 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'Angel-HP.keystoneaquaria.com' A
Mar  6 20:51:53 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'Angel-HP.keystoneaquaria.com' TXT
Mar  6 20:51:53 Cerberus named[1325]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
Mar  6 20:51:53 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': error: journal open failed: unexpected error
Mar  6 20:51:53 Cerberus kernel: [  456.498065] type=1400 audit(1394157113.645:24): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/db.keystoneaquaria.com.jnl" pid=1327 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104
Mar  6 20:51:53 Cerberus dhcpd: DHCPREQUEST for 192.168.1.32 from 5c:ac:4c:60:ad:64 (Angel-HP) via p2p1
Mar  6 20:51:53 Cerberus dhcpd: DHCPACK on 192.168.1.32 to 5c:ac:4c:60:ad:64 (Angel-HP) via p2p1
Mar  6 20:51:53 Cerberus dhcpd: Unable to add forward map from Angel-HP.keystoneaquaria.com. to 192.168.1.32: SERVFAIL
Mar  6 20:52:07 Cerberus named[1325]: client 127.0.0.1#43437: signer "rndc-key" approved
Mar  6 20:52:07 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'Randy-HP.keystoneaquaria.com' A
Mar  6 20:52:07 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': adding an RR at 'Randy-HP.keystoneaquaria.com' TXT
Mar  6 20:52:07 Cerberus named[1325]: /etc/bind/db.keystoneaquaria.com.jnl: create: permission denied
Mar  6 20:52:07 Cerberus named[1325]: client 127.0.0.1#43437: updating zone 'keystoneaquaria.com/IN': error: journal open failed: unexpected error
Mar  6 20:52:07 Cerberus kernel: [  470.139063] type=1400 audit(1394157127.309:25): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/db.keystoneaquaria.com.jnl" pid=1330 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104
Mar  6 20:52:07 Cerberus dhcpd: DHCPREQUEST for 192.168.1.22 from 20:16:d8:34:4d:9f (Randy-HP) via p2p1
Mar  6 20:52:07 Cerberus dhcpd: DHCPACK on 192.168.1.22 to 20:16:d8:34:4d:9f (Randy-HP) via p2p1
Mar  6 20:52:07 Cerberus dhcpd: Unable to add forward map from Randy-HP.keystoneaquaria.com. to 192.168.1.22: SERVFAIL

```
```

randy@Cerberus:/var/cache/bind$ ls -l
total 8
lrwxrwxrwx 1 root root  16 Mar  5 01:13 db.192 -> /etc/bind/db.192
lrwxrwxrwx 1 root root  32 Mar  5 01:12 db.keystoneaquaria.com -> /etc/bind/db.keystoneaquaria.com
-rw-r--r-- 1 bind bind 221 Mar  6 01:02 managed-keys.bind
-rw-r--r-- 1 bind bind 512 Mar  6 01:02 managed-keys.bind.jnl
randy@Cerberus:/var/cache/bind$

```
```

randy@Cerberus:/etc/bind$ ls -l
total 60
-rw-r--r-- 1 bind bind 2389 Oct 10  2012 bind.keys
-rw-r--r-- 1 bind bind  237 Oct 10  2012 db.0
-rw-r--r-- 1 bind bind  271 Oct 10  2012 db.127
-rw-r--r-- 1 bind bind  325 Mar  5 01:11 db.192
-rw-r--r-- 1 bind bind  237 Oct 10  2012 db.255
-rw-r--r-- 1 bind bind  353 Oct 10  2012 db.empty
-rw-r--r-- 1 bind bind  272 Mar  5 20:12 db.keystoneaquaria.com
-rw-r--r-- 1 bind bind  270 Oct 10  2012 db.local
-rw-r--r-- 1 bind bind 3048 Mar  5 16:42 db.root
-rw-r--r-- 1 bind bind  463 Oct 10  2012 named.conf
-rw-r--r-- 1 bind bind  490 Oct 10  2012 named.conf.default-zones
-rw-r--r-- 1 bind bind  577 Mar  6 14:02 named.conf.local
-rw-r--r-- 1 bind bind  940 Mar  6 00:59 named.conf.options
-rwxr-xr-x 1 bind bind   77 Mar  5 00:55 rndc.key
-rw-r--r-- 1 bind bind 1317 Oct 10  2012 zones.rfc1918
randy@Cerberus:/etc/bind$
```

---

### Post by lisati on 2014-03-06
@dispair1981: Please enclose your quotes of terminal output with [noparse]```
 and 
```[/noparse], doing so can help readability.

---

### Post by dispair1981 on 2014-03-06
Sorry, I was able to resolve the problem however.  I found this post [http://ubuntuforums.org/archive/index.php/t-1658873.html](http://ubuntuforums.org/archive/index.php/t-1658873.html) at the bottom it states that the folders should be "/var/lib/bind/zones" I created links with ```
sudo ln -sf /etc/bind/db* /var/lib/bind/
``` and restarted the server.  Everything is now working properly except the gateway that is static and need an appropriate A record setup.

Thank you for your help, I would not have gotten to this resolution without you.

---

