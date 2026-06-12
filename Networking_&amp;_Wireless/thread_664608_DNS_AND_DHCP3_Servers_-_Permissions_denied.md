---
title: "DNS AND DHCP3 Servers - Permissions denied"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by www.floranet.eu on 2008-01-11
I'm trying to config a server with Bind and DHCP server. All the things are working properly only i'm having an issu of updating the ip on the bind zone. My permissions on the folder and files are in the user bind... I'm loosing my head with this issue... Can anyone help me? 

Shortly: secret pass is correct.

List logs:

BIND
Jan 11 16:04:50 gateway named[6161]: starting BIND 9.3.2 -u bind
Jan 11 16:04:50 gateway named[6161]: found 1 CPU, using 1 worker thread
Jan 11 16:04:50 gateway named[6161]: loading configuration from '/etc/bind/named.conf'
Jan 11 16:04:50 gateway named[6161]: listening on IPv4 interface lo, 127.0.0.1#53
Jan 11 16:04:50 gateway named[6161]: listening on IPv4 interface eth0, 10.128.64.2#53
Jan 11 16:04:50 gateway named[6161]: listening on IPv4 interface eth1, 192.168.128.1#53
Jan 11 16:04:50 gateway named[6161]: command channel listening on 127.0.0.1#953
Jan 11 16:04:50 gateway named[6161]: zone 0.in-addr.arpa/IN: loaded serial 1
Jan 11 16:04:50 gateway named[6161]: zone 127.in-addr.arpa/IN: loaded serial 1
Jan 11 16:04:50 gateway named[6161]: zone 128.168.192.in-addr.arpa/IN: loaded serial 2007042501
Jan 11 16:04:50 gateway named[6161]: zone 255.in-addr.arpa/IN: loaded serial 1
Jan 11 16:04:50 gateway named[6161]: zone museupioxii.ca/IN: loaded serial 2007042501
Jan 11 16:04:50 gateway named[6161]: zone localhost/IN: loaded serial 1
Jan 11 16:04:50 gateway named[6161]: running
[COLOR=Red]Jan 11 16:05:00 gateway named[6161]: client 192.168.128.1#32778: update 'museupioxii.ca/IN' denied

DHCP
[/COLOR]Jan 11 16:05:00 gateway dhcpd: Unable to add forward map from postoesc01.museupioxii.ca. to 192.168.128.25: timed out
Jan 11 16:05:00 gateway dhcpd: DHCPREQUEST for 192.168.128.25 from 00:13:8f:9f:14:7e (postoesc01) via eth1
Jan 11 16:05:00 gateway dhcpd: DHCPACK on 192.168.128.25 to 00:13:8f:9f:14:7e (postoesc01) via eth1
[COLOR=Red]Jan 11 16:05:02 gateway named[6161]: client 192.168.128.1#32778: update 'museupioxii.ca/IN' denied
Jan 11 16:05:02 gateway dhcpd: Unable to add forward map from postoesc01.museupioxii.ca. to 192.168.128.25: timed out[/COLOR]
Jan 11 16:05:02 gateway dhcpd: DHCPREQUEST for 192.168.128.25 from 00:13:8f:9f:14:7e (postoesc01) via eth1
Jan 11 16:05:02 gateway dhcpd: DHCPACK on 192.168.128.25 to 00:13:8f:9f:14:7e (postoesc01) via eth1
Jan 11 16:10:02 gateway named[6161]: client 192.168.128.1#32778: update 'museupioxii.ca/IN' denied
Jan 11 16:10:02 gateway dhcpd: Unable to add forward map from postoesc01.museupioxii.ca. to 192.168.128.25: timed out
Jan 11 16:10:02 gateway dhcpd: DHCPREQUEST for 192.168.128.25 from 00:13:8f:9f:14:7e (postoesc01) via eth1
Jan 11 16:10:02 gateway dhcpd: DHCPACK on 192.168.128.25 to 00:13:8f:9f:14:7e (postoesc01) via eth1
Jan 11 16:15:02 gateway named[6161]: client 192.168.128.1#32778: update 'museupioxii.ca/IN' denied
Jan 11 16:15:02 gateway dhcpd: Unable to add forward map from postoesc01.museupioxii.ca. to 192.168.128.25: timed out
Jan 11 16:15:03 gateway dhcpd: DHCPREQUEST for 192.168.128.25 from 00:13:8f:9f:14:7e (postoesc01) via eth1
Jan 11 16:15:03 gateway dhcpd: DHCPACK on 192.168.128.25 to 00:13:8f:9f:14:7e (postoesc01) via eth1
Files:

[COLOR=Red]named.conf.options[/COLOR]

options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you might need to uncomment the query-source
    // directive below.  Previous versions of BIND always asked
    // questions using port 53, but BIND 8.1 and later use an unprivileged
    // port by default.

    query-source address * port 53;

       //default-key "rndc-key";
       //default-server 127.0.0.1;
       //default-port 953;

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    forwarders {
         10.128.64.1;
    };
    
    auth-nxdomain no;    # conform to RFC1035
    
    allow-query { 
        192.168.128.0/24;
        127.0.0.0/24;     
    };
        allow-transfer { none; };
};

[COLOR=Black][COLOR=Red]named.conf[/COLOR]

[COLOR=DimGray]// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
    type hint;
    file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
    type master;
    file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
    type master;
    file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
    type master;
    file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
    type master;
    file "/etc/bind/db.255";
};
 
// zone "com" { type delegation-only; };
// zone "net" { type delegation-only; };

// From the release notes:
//  Because many of our users are uncomfortable receiving undelegated answers
//  from root or top level domains, other than a few for whom that behaviour
//  has been trusted and expected for quite some length of time, we have now
//  introduced the "root-delegations-only" feature which applies delegation-only
//  logic to all top level domains, and to the root domain.  An exception list
//  should be specified, including "MUSEUM" and "DE", and any other top level
//  domains from whom undelegated responses are expected and trusted.
// root-delegation-only exclude { "DE"; "MUSEUM"; };

include "/etc/bind/named.conf.local";
controls {
    inet 127.0.0.1 port 953 allow { 127.0.0.1; } keys { rndc-key; };
    //inet 192.168.128.1 port 953 allow { 192.168.128.1; } keys { rndc-key; };
    };

[COLOR=Red]named.conf.local[/COLOR]

//
// Do any local configuration here
//

zone "museupioxii.ca" {
    type master;
    file "/etc/bind/db.museupioxii.ca";
    allow-update { key "rndc-key"; };
    allow-transfer { 
        192.168.128.1;
        127.0.0.1;
    };
    notify yes;
};

zone "128.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.128.168.192";
    allow-update { key "rndc-key"; };
    notify yes;
};

include "/etc/bind/rndc.key";

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


:confused::confused::confused::confused::confused::(:(:(
[/COLOR][/COLOR]

---

