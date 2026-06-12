---
title: "Non-Reverse PTR records not transferred correctly from Windows 2016 to Bind 9?"
date: 2018-11-05
forum: Networking &amp; Wireless
---

### Post by bell.colin on 2018-11-05
Using several AD-Integrated zone (running server 2016) with Ubuntu 16.04 running as Bind secondaries (running Bind 9.x) which are used by all client machines as dns servers.

It appears some PTR records in the forward lookup zones don't transfer or can't be queried by clients using the ubuntu servers as their name server.

I'm setting up these records using [these]("https://www.printerlogic.com/printer-installer/support/user-guide-15-1/mobile-printing/ios/") (under step #6) and the records resolve when using the 2016 servers in nslookup but fail when using the ubuntu ones. (all other queries work and have been working for years)

Here are examples of test and code snippets: (with domain names changed/some files filtered)

Ubuntu DNS Server: 10.1.0.31
Win 2016 DNS AD Server: 10.1.101.11
Print Server: 10.1.0.67


nslookup from client using server 2016 dns server:
```

C:\Users\username>nslookup airprint.domain.com 10.1.101.11
Server:  ADS01.domain.com
Address:  10.1.101.11


Name:    airprint.domain.com
Address:  10.1.0.67

```


nslookup from client using ubuntu dns server:
```

C:\Users\username>nslookup airprint.domain.com 10.1.0.31
Server:  NS01.domain.com
Address:  10.1.0.31


*** NS01.domain.com can't find airprint.domain.com: Non-existent domain

```


Section from zone file on ubuntu dns server:
```

<rest of file removed>
$ORIGIN _udp.domain.com.lb._dns-sd              PTR     airprint.domain.com.
...
<rest of file removed>
...
$TTL 1800       ; 30 minutes
airprint                NS      airprint
                        A       10.1.0.67
<rest of file removed>

```


PTR service record from 2016 server:
[ATTACH=CONFIG]281548[/ATTACH]


Delegation service record from 2016 server:
[ATTACH=CONFIG]281549[/ATTACH]


named.conf from ubuntu dns server:
```

// This is the primary configuration file for the BIND DNS server named.//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local


include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";


include "/etc/bind/named.conf.acl";
include "/etc/bind/named.conf.<removed>-zones";
include "/etc/bind/named.conf.other-zones";
include "/etc/bind/named.conf.logging";

```


named.conf.options from ubuntu dns server:
```

options {        directory "/var/cache/bind";


        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113


        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.


        // forwarders {
        //      0.0.0.0;
        // };


        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================


        dnssec-enable no;
// ##   dnssec-validation auto;
        dnssec-validation no;


        auth-nxdomain no;    # conform to RFC1035
// ##   listen-on-v6 { any; };
        listen-on-v6 { none; };


        forwarders {
                <removed_isp-dns>;
        };


        allow-query {
#               0.0.0.0/0;
                10.0.0.0/8;
                192.168.0.0/16;
                localhost;
                localnets;
        };


        allow-update-forwarding {
                10.0.0.0/8;
                localhost;
                localnets;
        };


};

```


named.conf.<removed>-zones from ubuntu dns server: (filtered)
```

//// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


## BEGIN LOGGING


#       Separate Log file in '/var/log/':
#               See "http://camillelemouellic.blog.com/2014/02/12/linux-write-dhcpd-logs-to-its-own-file-and-not-in-syslog-with-rsyslog/"
#
#       Logrotate: (/etc/logrotate.d/dhcpd)
#               See "https://www.debian-administration.org/article/117/Creating_logfile_archives_with_logrotate"


## END LOGGING


########################################
##### BEGIN Forward Zones #####
########################################


## BEGIN "domain.com" forward zone
        zone "domain.com" IN {
                type slave;
                file "domain.com.zone";
                masterfile-format text;
                masters { master-servers; };
                allow-transfer { xfer-servers; };
        };
## END "domain.com" forward zone
<rest of file removed>

```

Is there a work-around for this or does bind not support these records?

---

