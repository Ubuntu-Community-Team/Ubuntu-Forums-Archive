---
title: "DNS Bind Resolution"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by Swigbert on 2007-11-16
Walked into a problem....

Windows network with Slackware 9 DNS configured as a split DNS at central office with two remote sites. All sites have their own routers(Cisco) handing out DHCP.  They connect through central office to receive their internet access and email and in the name resolution, inside & out.

Slackware DNS box failed due to hardware problems corrupting the mbr. I built a ubuntu 7.10 server with DNS. I was able to mount the old hd on the new box and copy the necessary files into the new ubuntu DNS scenario. Central office came online immediately and all seemed great. I say seemed great because I was in the central office.

Remote offices and their clients were set to automatically obtain their DNS settings. Email, which is on the LAN works but internet access is failing. Changing the DNS settings to external servers allows internet access but fails to retrieve email. Obviously having the clients continually changing their DNS settings to perform work is out of the question.

Named.conf has not been altered. Named.conf.local has the zones
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

// --------------ACL/Address Match Lists to specify DNS clients, followed by zones

acl esco-inside {
        192.168.0.0/16;
        10.0.0.0/8;
        127.0.0.0/8;
        };

# This is the zone definition

//-------------Private Zones for internal hosts

view "esco-inside" {

        match-clients { "esco-inside"; };
        recursion yes;

        zone "escocommunications.com." {
                type master;
                file "/etc/bind/zones/escocommunications.com.db";
        };

        zone "localhost" {
                type master;
                file "/etc/bind/zones/localhost.zone";
                allow-update {none; };
        };

        zone "0-254.1.168.192.in-addr.arpa" {
                type master;
                file "/etc/bind/zones/192.168.1.0-254.rev";
                allow-update { none; };
        };

        zone "0.0.127.in-addr.arpa" {
                type master;
                file "/etc/bind/zones/named.local";
                allow-update { none; };
        };

// ------------Root Hints (outside resolution)

        zone "." IN {
                type hint;
                file "/etc/bind/named.cache";
        };

};

// ---------Public Zones for ESCO hosts

view "esco-outside" {

        match-clients {any ;};          //implicit matches the outside
        recursion no;                   //no recursive lookups from non-ESCO DNS clients

        zone "escocommunications.com." {
                type master;
                file "/etc/bind/zones/public/escocommunications.com";
        };

        zone "0-32.14.78.68.in-addr.arpa" {
                type master;
                file "/etc/bind/zones/public/68.78.14.0-32.rev";
        };

        zone "localhost" {
                type master;
                file "/etc/bind/zones/localhost.zone";
                allow-update { none; };
        };

        zone "0.0.127.in-addr.arpa" {
                type master;
                file "/etc/bind/zones/named.local";
                allow-update { none; };
        };
};

brent@shiny:/etc/bind$

```

What am I missing?

---

