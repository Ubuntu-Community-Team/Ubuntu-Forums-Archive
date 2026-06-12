---
title: "DNS &amp; DHCP configuration"
date: 2016-07-22
forum: Networking &amp; Wireless
---

### Post by Al Grant on 2016-07-22
Good Morning,

I am trying to setup DNS and DHCP updating of DNS on my home LAN, but I think my configuration is not right because I do not believe DHCP is updating DNS. I can however browser the internet just fine, so forward resolving is working.

subnet: 192.168.55.0
gateway: 192.168.55.1
ubuntuws01 : 192.168.55.254 (DNS bind9 and DHCP isc-dhcp-server running on this host)
domain: lan.geekhelp.co.nz

I have a few coomputers on the LAN, mainly windows.

Conf files:
**named.conf**
```


include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

logging{
  channel simple_log {
    file "/var/log/named/bind.log" versions 3 size 5m;
    severity debug;
    print-time yes;
    print-severity yes;
    print-category yes;
  };
  category default{
    simple_log;
  };
};

```

**named.conf.options**
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
                203.109.191.1;
                203.118.191.1;
         };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

**named.conf.local**
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

key "DHCP_UPDATER" {
        algorithm HMAC-MD5.SIG-ALG.REG.INT;
        secret "ZTc**********SuyA==";
};

controls {
        inet 127.0.0.1 allow { localhost; 192.168.55.254; } keys { "DHCP_UPDATER"; };
};

zone "lan.geekhelp.co.nz" {
        type master;
        file "/etc/bind/db.geekhelp.local";
        allow-update {key "DHCP_UPDATER"; };
        notify yes;
};

zone "55.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
        allow-update {key "DHCP_UPDATER"; };
        notify yes;
};

```

**db.geekhelp.local**
```

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ubuntuws01.lan.geekhelp.co.nz. algrant.local. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ubuntuws01.lan.geekhelp.co.nz.
@       IN      A       127.0.0.1
@       IN      AAAA    ::1

; *** A RECORDS ***

ubuntuws01                      IN      A       192.168.55.254
draytek                         IN      A       192.168.55.1
ubuntuws01.lan.geekhelp.co.nz   IN      A       192.168.55.254
lan.geekhelp.co.nz              IN      A       127.0.0.1

; *** CNAME RECORDS ***
ns                              IN      CNAME   ubuntuws01

```

**syslog after restart of both services**
```

Jul 23 11:58:01 UBUNTUWS01 named[23433]: ----------------------------------------------------
Jul 23 11:58:01 UBUNTUWS01 named[23433]: BIND 9 is maintained by Internet Systems Consortium,
Jul 23 11:58:01 UBUNTUWS01 named[23433]: Inc. (ISC), a non-profit 501(c)(3) public-benefit
Jul 23 11:58:01 UBUNTUWS01 named[23433]: corporation.  Support and training for BIND 9 are
Jul 23 11:58:01 UBUNTUWS01 named[23433]: available at https://www.isc.org/support
Jul 23 11:58:01 UBUNTUWS01 named[23433]: ----------------------------------------------------
Jul 23 11:58:01 UBUNTUWS01 named[23433]: adjusted limit on open files from 4096 to 1048576
Jul 23 11:58:01 UBUNTUWS01 named[23433]: found 2 CPUs, using 2 worker threads
Jul 23 11:58:01 UBUNTUWS01 named[23433]: using 2 UDP listeners per interface
Jul 23 11:58:01 UBUNTUWS01 named[23433]: using up to 4096 sockets
Jul 23 11:58:01 UBUNTUWS01 named[23433]: loading configuration from '/etc/bind/named.conf'
Jul 23 11:58:01 UBUNTUWS01 named[23433]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Jul 23 11:58:01 UBUNTUWS01 named[23433]: initializing GeoIP Country (IPv4) (type 1) DB
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GEO-106FREE 20160408 Bu
Jul 23 11:58:01 UBUNTUWS01 named[23433]: initializing GeoIP Country (IPv6) (type 12) DB
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GEO-106FREE 20160408 Bu
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP City (IPv4) (type 2) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP City (IPv4) (type 6) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP City (IPv6) (type 30) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP City (IPv6) (type 31) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP Region (type 3) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP Region (type 7) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP ISP (type 4) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP Org (type 5) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP AS (type 9) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP Domain (type 11) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: GeoIP NetSpeed (type 10) DB not available
Jul 23 11:58:01 UBUNTUWS01 named[23433]: using default UDP/IPv4 port range: [32768, 60999]
Jul 23 11:58:01 UBUNTUWS01 named[23433]: using default UDP/IPv6 port range: [32768, 60999]
Jul 23 11:58:01 UBUNTUWS01 named[23433]: listening on IPv6 interfaces, port 53
Jul 23 11:58:01 UBUNTUWS01 named[23433]: listening on IPv4 interface lo, 127.0.0.1#53
Jul 23 11:58:01 UBUNTUWS01 named[23433]: listening on IPv4 interface enp1s0, 192.168.55.254#53
Jul 23 11:58:01 UBUNTUWS01 named[23433]: generating session key for dynamic DNS
Jul 23 11:58:01 UBUNTUWS01 named[23433]: sizing zone task pool based on 7 zones
Jul 23 11:58:01 UBUNTUWS01 named[23433]: using built-in root key for view _default
Jul 23 11:58:01 UBUNTUWS01 named[23433]: set up managed keys zone for view _default, file 'managed-keys.bind'
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 10.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 16.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 17.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 18.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 19.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 20.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 21.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 22.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 23.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 24.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 25.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 26.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 27.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 28.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 29.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 30.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 31.172.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 168.192.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 64.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 65.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 66.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 67.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 68.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 69.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 70.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 71.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 72.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 73.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 74.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 75.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 76.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 77.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 78.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 79.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 80.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 81.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 82.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 83.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 84.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 85.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 86.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 87.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 88.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 89.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 90.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 91.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 92.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 93.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 94.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 95.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 96.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 97.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 98.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 99.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 100.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 101.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 102.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 103.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 104.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 105.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 106.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 107.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 108.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 109.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 110.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 111.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 112.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 113.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 114.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 115.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 116.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 117.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 118.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 119.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 120.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 121.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 122.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 123.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 124.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 125.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 126.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 127.100.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: D.F.IP6.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 8.E.F.IP6.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 9.E.F.IP6.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: A.E.F.IP6.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: B.E.F.IP6.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: automatic empty zone: EMPTY.AS112.ARPA
Jul 23 11:58:01 UBUNTUWS01 named[23433]: command channel listening on 127.0.0.1#953
Jul 23 11:58:08 UBUNTUWS01 systemd[1]: Stopping ISC DHCP IPv4 server...
Jul 23 11:58:08 UBUNTUWS01 systemd[1]: Stopped ISC DHCP IPv4 server.
Jul 23 11:58:08 UBUNTUWS01 systemd[1]: Started ISC DHCP IPv4 server.
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Internet Systems Consortium DHCP Server 4.3.3
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Copyright 2004-2015 Internet Systems Consortium.
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: Internet Systems Consortium DHCP Server 4.3.3
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: Copyright 2004-2015 Internet Systems Consortium.
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: All rights reserved.
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: For info, please visit https://www.isc.org/software/dhcp/
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: All rights reserved.
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: For info, please visit https://www.isc.org/software/dhcp/
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Config file: /etc/dhcp/dhcpd.conf
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Database file: /var/lib/dhcp/dhcpd.leases
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: Config file: /etc/dhcp/dhcpd.conf
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: Database file: /var/lib/dhcp/dhcpd.leases
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: PID file: /run/dhcp-server/dhcpd.pid
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: PID file: /run/dhcp-server/dhcpd.pid
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: Wrote 8 leases to leases file.
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Internet Systems Consortium DHCP Server 4.3.3
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Copyright 2004-2015 Internet Systems Consortium.
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: All rights reserved.
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: For info, please visit https://www.isc.org/software/dhcp/
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Wrote 8 leases to leases file.
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Listening on LPF/enp1s0/bc:5f:f4:a3:86:42/192.168.55.0/24
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Sending on   LPF/enp1s0/bc:5f:f4:a3:86:42/192.168.55.0/24
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: Listening on LPF/enp1s0/bc:5f:f4:a3:86:42/192.168.55.0/24
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: Sending on   LPF/enp1s0/bc:5f:f4:a3:86:42/192.168.55.0/24
Jul 23 11:58:08 UBUNTUWS01 sh[23457]: Sending on   Socket/fallback/fallback-net
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Sending on   Socket/fallback/fallback-net
Jul 23 11:58:08 UBUNTUWS01 dhcpd[23457]: Server starting service.
algrant@ubuntuws01:/etc/bind$

```

**syslog after client tried to register**
```

Jul 23 11:59:31 UBUNTUWS01 dhcpd[23457]: DHCPREQUEST for 192.168.55.103 from 40:25:c2:84:3a:cc (GRANTLP01) via enp1s0
Jul 23 11:59:31 UBUNTUWS01 dhcpd[23457]: DHCPACK on 192.168.55.103 to 40:25:c2:84:3a:cc (GRANTLP01) via enp1s0
Jul 23 11:59:31 UBUNTUWS01 dhcpd[23457]: Unable to add forward map from GRANTLP01.lan.geekhelp.co.nz. to 192.168.55.103: SERVFAIL

```

And finally **dhcpd.conf**
```

ddns-updates on;
ddns-update-style interim;

ddns-domainname "lan.geekhelp.co.nz.";
ddns-rev-domainname "in-addr.arpa.";

update-static-leases on;
allow unknown-clients;
use-host-decl-names on;
key DHCP_UPDATER {
        algorithm HMAC-MD5.SIG-ALG.REG.INT;
        secret "ZTcS******************A==";
}

option domain-name "lan.geekhelp.co.nz";
option domain-name-servers ubuntuws01.lan.geekhelp.co.nz;

default-lease-time 1814400;
max-lease-time 1814400;

log-facility local7;

# ***************************
# ******* DNS ZONES *********
# ***************************

zone lan.geekhelp.co.nz. {
        primary 127.0.0.1;
        key DHCP_UPDATER;
}

zone 55.168.192.in-addr.arpa. {
        primary 127.0.0.1;
        key DHCP_UPDATER;
}

# **************************************
# ********* GEEKHELP LAN SCOPE *********
# **************************************

subnet 192.168.55.0 netmask 255.255.255.0 {
        range 192.168.55.100 192.168.55.200;
        option subnet-mask 255.255.255.0;
        option routers 192.168.55.1;
        option domain-name-servers 192.168.55.254;
        option domain-name "lan.geekhelp.co.nz";
        option domain-search "lan.geekhelp.co.nz";
        ddns-domainname "lan.geekhelp.co.nz.";
        ddns-rev-domainname "in-addr.arpa.";
}

```

I hope this helps and someone can point me in the right direction.

Thanks in advance

-Al

---

### Post by Al Grant on 2016-07-22
BTW: These files all reside in /etc/bind.

These are the permissions:

```

algrant@ubuntuws01:/etc/bind$ ls -l
total 68
-rw-r--r-- 1 root root 2389 Apr 27 13:58 bind.keys
-rw-r--r-- 1 root root  237 Apr 27 13:58 db.0
-rw-r--r-- 1 root root  271 Apr 27 13:58 db.127
-rw-r--r-- 1 root bind  366 Jul 23 00:03 db.192
-rw-r--r-- 1 root root  237 Apr 27 13:58 db.255
-rw-r--r-- 1 root root  353 Apr 27 13:58 db.empty
-rw-r--r-- 1 root bind  532 Jul 23 00:41 db.geekhelp.local
-rw-r--r-- 1 root root  270 Apr 27 13:58 db.local
-rw-r--r-- 1 root root 3171 Apr 27 13:58 db.root
-rw-r--r-- 1 root bind  931 Jul 23 12:54 named.conf
-rw-r--r-- 1 root bind  490 Apr 27 13:58 named.conf.default-zones
-rw-r----- 1 root bind  632 Jul 23 12:55 named.conf.local
-rw-r--r-- 1 root bind  906 Jul 19 13:08 named.conf.options
-rw-r--r-- 1 root bind  581 Jul 23 12:28 rndc.conf
-rw-r--r-- 1 bind bind  112 Jul 23 12:29 rndc.key
-rw-r----- 1 bind bind   77 Jul 19 13:03 rndc.key.backup
-rw-r--r-- 1 root root 1317 Apr 27 13:58 zones.rfc1918
algrant@ubuntuws01:/etc/bind$

```

---

### Post by papibe on 2016-07-22
Hi Al Grant.

Copy or move these files:
```
/etc/bind/db.geekhelp.local
/etc/bind/db.192"
```
from /etc/bind to /var/cache/bind (because AppArmor only allows write access inside it, ref [here]("https://help.ubuntu.com/community/BIND9ServerHowto#Secondary_Master_Server_configuration")):
```
/var/cache/bind/db.geekhelp.local
/var/cache/bind/db.192"
```
and update your named.conf.local, so it points to the new location. Don't forget to increase your serial fields in db.geekhelp.local, and in db.192 (which you didn't paste btw). 

Restart the services.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Al Grant on 2016-07-22
Increasing the verbosity of the debug to level 1 gives a better hint at the error:

```

23-Jul-2016 13:41:09.895 update: info: client 127.0.0.1#17369/key rndc-key: updating zone 'lan.geekhelp.co.nz/IN': adding an RR at 'GRANTLP01.lan.geekhelp.co.nz' A 192.168.55.103
23-Jul-2016 13:41:09.896 update: info: client 127.0.0.1#17369/key rndc-key: updating zone 'lan.geekhelp.co.nz/IN': adding an RR at 'GRANTLP01.lan.geekhelp.co.nz' TXT "3117c8e57da9ed449ad55e9d4b058726a7"
23-Jul-2016 13:41:09.896 general: debug 1: journal file /etc/bind/db.geekhelp.local.jnl does not exist, creating it
23-Jul-2016 13:41:09.896 general: error: /etc/bind/db.geekhelp.local.jnl: create: permission denied
23-Jul-2016 13:41:09.896 update: info: client 127.0.0.1#17369/key rndc-key: updating zone 'lan.geekhelp.co.nz/IN': error: journal open failed: unexpected error
23-Jul-2016 13:41:09.896 database: debug 1: decrement_reference: delete from rbt: 0x7f30a7229390 GRANTLP01.lan.geekhelp.co.nz


```

---

### Post by Al Grant on 2016-07-22
I tried to copy those files, but I think there is already a symlink in place:

```

algrant@ubuntuws01:/etc/bind$ sudo cp /etc/bind/db.geekhelp.local /var/cache/bind/db.geekhelp.local
[sudo] password for algrant:
cp: '/etc/bind/db.geekhelp.local' and '/var/cache/bind/db.geekhelp.local' are the same file
algrant@ubuntuws01:/etc/bind$ sudo cp /etc/bind/db.192 /var/cache/bind/db.192
cp: '/etc/bind/db.192' and '/var/cache/bind/db.192' are the same file
algrant@ubuntuws01:/etc/bind$

```

Also re my above error with the **error: /etc/bind/db.geekhelp.local.jnl: create: permission denied** I have fixed this by changing permissions chown bind:bind bind

But I still think things are not right as dig ubuntuws01 does not have a answer.

Cheers

-Al

---

### Post by papibe on 2016-07-22
EDIT: this was for your log post.

Yes, permission problems, as explained in the previous post.

Did you solve your problem?

Regards.

---

### Post by papibe on 2016-07-22
Stop bind, and dhcp.

Force the copy with cp -f, or delete the copies on /var/cache/bind, and copy them again.

The important thing is that you update your config file, to point to /var/cache/bind instead of /etc/bind

Regards.

---

### Post by Al Grant on 2016-07-22
They dont acutally exist tho - they are links

```

algrant@ubuntuws01:/var/cache/bind$ ls -l
total 84
lrwxrwxrwx 1 root root    16 Jul 23 13:03 db.192 -> /etc/bind/db.192
lrwxrwxrwx 1 root root    27 Jul 23 13:03 db.geekhelp.local -> /etc/bind/db.geekhelp.local
-rw-r--r-- 1 bind bind   821 Jul 23 14:12 managed-keys.bind
-rw-r--r-- 1 bind bind   512 Jul 23 14:12 managed-keys.bind.jnl
-rw-r--r-- 1 bind bind 74833 Jul 21 15:29 named_dump.db
algrant@ubuntuws01:/var/cache/bind$

```

What should I do?

---

### Post by papibe on 2016-07-22
Oh I see.

That may work, but point to those links on your config files 

named.conf.local
```

...
zone "lan.geekhelp.co.nz" {
        ...
        file **"/var/cache/bind/db.geekhelp.local"**;
        ...
};
...
zone "55.168.192.in-addr.arpa" {
        ...
        file** "/var/cache/bind/db.192"**;
        ...};
```
and don't forget to increase your serials ;)

---

### Post by Al Grant on 2016-07-22
Okay....looking better:

```

23-Jul-2016 14:23:22.598 update-security: info: client 127.0.0.1#30025/key rndc-key: signer "rndc-key" approved
23-Jul-2016 14:23:22.598 update: info: client 127.0.0.1#30025/key rndc-key: updating zone 'lan.geekhelp.co.nz/IN': adding an RR at 'GRANTLP01.lan.geekhelp.co.nz' A 192.168.55.103
23-Jul-2016 14:23:22.598 update: info: client 127.0.0.1#30025/key rndc-key: updating zone 'lan.geekhelp.co.nz/IN': adding an RR at 'GRANTLP01.lan.geekhelp.co.nz' TXT "3117c8e57da9ed449ad55e9d4b058726a7"
23-Jul-2016 14:23:22.807 general: debug 1: zone_needdump: zone lan.geekhelp.co.nz/IN: enter
23-Jul-2016 14:23:22.807 general: debug 1: zone_settimer: zone lan.geekhelp.co.nz/IN: enter
23-Jul-2016 14:23:22.807 general: debug 1: zone_settimer: zone lan.geekhelp.co.nz/IN: enter
23-Jul-2016 14:23:22.807 general: debug 1: zone_timer: zone lan.geekhelp.co.nz/IN: enter
23-Jul-2016 14:23:22.807 general: debug 1: zone_maintenance: zone lan.geekhelp.co.nz/IN: enter
23-Jul-2016 14:23:22.807 general: debug 1: zone_settimer: zone lan.geekhelp.co.nz/IN: enter
23-Jul-2016 14:23:22.860 resolver: debug 1: fetch: www.msftncsi.com/A
23-Jul-2016 14:23:22.860 resolver: debug 1: fetch: ./NS
23-Jul-2016 14:23:22.874 database: debug 1: decrement_reference: delete from rbt: 0x7f78b004ff88 www.msftncsi.com.edgesuite.net
23-Jul-2016 14:23:22.874 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0060010 www.msftncsi.com
23-Jul-2016 14:23:22.874 resolver: debug 1: fetch: com/DS
23-Jul-2016 14:23:22.887 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0058078 com
23-Jul-2016 14:23:22.887 resolver: debug 1: fetch: msftncsi.com/DS
23-Jul-2016 14:23:22.901 resolver: debug 1: fetch: com/DNSKEY
23-Jul-2016 14:23:22.914 resolver: debug 1: fetch: www.msftncsi.com.edgesuite.net/A
23-Jul-2016 14:23:22.932 database: debug 1: decrement_reference: delete from rbt: 0x7f78b004ff88 www.msftncsi.com.edgesuite.net
23-Jul-2016 14:23:22.932 resolver: debug 1: fetch: net/DS
23-Jul-2016 14:23:22.945 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0058148 net
23-Jul-2016 14:23:22.946 resolver: debug 1: fetch: edgesuite.net/DS
23-Jul-2016 14:23:22.960 resolver: debug 1: fetch: net/DNSKEY
23-Jul-2016 14:23:22.974 resolver: debug 1: fetch: a1961.g2.akamai.net/A
23-Jul-2016 14:23:22.988 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0060088 a1961.g2.akamai.net
23-Jul-2016 14:23:22.988 resolver: debug 1: fetch: akamai.net/DS
23-Jul-2016 14:23:23.950 resolver: debug 1: fetch: geover-prod.do.dsp.mp.microsoft.com/A
23-Jul-2016 14:23:23.950 resolver: debug 1: fetch: ./NS
23-Jul-2016 14:23:23.963 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0067010 geover-prod.do.dsp.mp.microsoft.com
23-Jul-2016 14:23:23.963 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0066f80 geover-prod.dodsp.mp.microsoft.com.nsatc.net
23-Jul-2016 14:23:23.963 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0066f80 prod.do.dsp.mp.microsoft.com.edgekey.net
23-Jul-2016 14:23:23.963 resolver: debug 1: fetch: microsoft.com/DS
23-Jul-2016 14:23:23.978 resolver: debug 1: fetch: geover-prod.dodsp.mp.microsoft.com.nsatc.net/A
23-Jul-2016 14:23:23.991 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0066f80 geover-prod.dodsp.mp.microsoft.com.nsatc.net
23-Jul-2016 14:23:23.991 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0066f80 prod.do.dsp.mp.microsoft.com.edgekey.net
23-Jul-2016 14:23:23.991 resolver: debug 1: fetch: nsatc.net/DS
23-Jul-2016 14:23:24.006 resolver: debug 1: fetch: prod.do.dsp.mp.microsoft.com.edgekey.net/A
23-Jul-2016 14:23:24.006 resolver: debug 1: fetch: ./NS
23-Jul-2016 14:23:24.020 database: debug 1: decrement_reference: delete from rbt: 0x7f78b006c010 prod.do.dsp.mp.microsoft.com.edgekey.net
23-Jul-2016 14:23:24.020 resolver: debug 1: fetch: edgekey.net/DS
23-Jul-2016 14:23:24.034 resolver: debug 1: fetch: e1706.g.akamaiedge.net/A
23-Jul-2016 14:23:24.047 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0060088 e1706.g.akamaiedge.net
23-Jul-2016 14:23:24.047 resolver: debug 1: fetch: akamaiedge.net/DS
23-Jul-2016 14:23:24.164 resolver: debug 1: fetch: geo-prod.do.dsp.mp.microsoft.com/A
23-Jul-2016 14:23:24.178 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063400 geo-prod.do.dsp.mp.microsoft.com
23-Jul-2016 14:23:24.178 resolver: debug 1: fetch: geo-prod.dodsp.mp.microsoft.com.nsatc.net/A
23-Jul-2016 14:23:24.192 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063470 geo-prod.dodsp.mp.microsoft.com.nsatc.net
23-Jul-2016 14:23:24.192 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063470 au-1.ns.nsatc.net
23-Jul-2016 14:23:24.192 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063470 uk-1.ns.nsatc.net
23-Jul-2016 14:23:24.192 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0058218 g.ns.nsatc.net
23-Jul-2016 14:23:24.192 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0058218 l.ns.nsatc.net
23-Jul-2016 14:23:24.488 resolver: debug 1: fetch: licensing.mp.microsoft.com/A
23-Jul-2016 14:23:24.501 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00634e0 licensing.mp.microsoft.com
23-Jul-2016 14:23:24.501 database: debug 1: decrement_reference: delete from rbt: 0x7f78b006c010 licensing.md.mp.microsoft.com.akadns.net
23-Jul-2016 14:23:24.501 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0066140 licensing-asia.md.mp.microsoft.com.akadns.net
23-Jul-2016 14:23:24.501 resolver: debug 1: fetch: licensing.md.mp.microsoft.com.akadns.net/A
23-Jul-2016 14:23:24.516 database: debug 1: decrement_reference: delete from rbt: 0x7f78b006c010 licensing.md.mp.microsoft.com.akadns.net
23-Jul-2016 14:23:24.516 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0066140 licensing-asia.md.mp.microsoft.com.akadns.net
23-Jul-2016 14:23:24.516 resolver: debug 1: fetch: akadns.net/DS
23-Jul-2016 14:23:24.530 resolver: debug 1: fetch: licensing-asia.md.mp.microsoft.com.akadns.net/A
23-Jul-2016 14:23:24.544 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0060088 licensing-asia.md.mp.microsoft.com.akadns.net
23-Jul-2016 14:23:24.544 resolver: debug 1: fetch: hk2.licensing.md.mp.microsoft.com.akadns.net/A
23-Jul-2016 14:23:24.557 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0058280 hk2.licensing.md.mp.microsoft.com.akadns.net
23-Jul-2016 14:23:25.265 resolver: debug 1: fetch: kv401-prod.do.dsp.mp.microsoft.com/A
23-Jul-2016 14:23:25.265 resolver: debug 1: fetch: ./NS
23-Jul-2016 14:23:25.279 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00635c0 kv401-prod.do.dsp.mp.microsoft.com
23-Jul-2016 14:23:25.279 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00635c0 kv401-prod.dodsp.mp.microsoft.com.nsatc.net
23-Jul-2016 14:23:25.279 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00635c0 kv401-prod.do.dsp.mp.microsoft.com.edgekey.net
23-Jul-2016 14:23:25.280 resolver: debug 1: fetch: kv401-prod.dodsp.mp.microsoft.com.nsatc.net/A
23-Jul-2016 14:23:25.294 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063630 kv401-prod.dodsp.mp.microsoft.com.nsatc.net
23-Jul-2016 14:23:25.294 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063630 kv401-prod.do.dsp.mp.microsoft.com.edgekey.net
23-Jul-2016 14:23:25.294 resolver: debug 1: fetch: kv401-prod.do.dsp.mp.microsoft.com.edgekey.net/A
23-Jul-2016 14:23:25.308 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00636a0 kv401-prod.do.dsp.mp.microsoft.com.edgekey.net
23-Jul-2016 14:23:25.308 resolver: debug 1: fetch: e7589.g.akamaiedge.net/A
23-Jul-2016 14:23:25.320 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0058350 e7589.g.akamaiedge.net
23-Jul-2016 14:23:25.939 resolver: debug 1: fetch: win10.ipv6.microsoft.com/A
23-Jul-2016 14:23:25.953 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063710 win10.ipv6.microsoft.com
23-Jul-2016 14:23:25.953 resolver: debug 1: fetch: win10.ipv6.microsoft.com.nsatc.net/A
23-Jul-2016 14:23:25.967 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063780 win10.ipv6.microsoft.com.nsatc.net
23-Jul-2016 14:23:25.967 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063780 au-1.ns.nsatc.net
23-Jul-2016 14:23:25.967 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063780 uk-1.ns.nsatc.net
23-Jul-2016 14:23:25.967 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00583b8 g.ns.nsatc.net
23-Jul-2016 14:23:25.967 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00583b8 l.ns.nsatc.net
23-Jul-2016 14:23:29.489 resolver: debug 1: fetch: central.crashplan.com/A
23-Jul-2016 14:23:29.490 resolver: debug 1: fetch: ./NS
23-Jul-2016 14:23:29.503 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0060178 central.crashplan.com
23-Jul-2016 14:23:29.503 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00637f0 crashplan.com
23-Jul-2016 14:23:29.503 resolver: debug 1: fetch: crashplan.com/DS
23-Jul-2016 14:23:32.220 general: debug 1: zone_timer: managed-keys-zone : enter
23-Jul-2016 14:23:32.220 general: debug 1: zone_maintenance: managed-keys-zone : enter
23-Jul-2016 14:23:32.220 general: debug 1: zone_dump: managed-keys-zone : enter
23-Jul-2016 14:23:32.220 general: debug 1: zone_settimer: managed-keys-zone : enter
23-Jul-2016 14:23:32.220 general: debug 1: zone_gotwritehandle: managed-keys-zone : enter
23-Jul-2016 14:23:32.416 general: debug 1: dump_done: managed-keys-zone : enter
23-Jul-2016 14:23:32.416 general: debug 1: journal file managed-keys.bind.jnw does not exist, creating it
23-Jul-2016 14:23:38.191 resolver: debug 1: fetch: wdcp.microsoft.com/A
23-Jul-2016 14:23:38.191 resolver: debug 1: fetch: ./NS
23-Jul-2016 14:23:38.204 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00583b8 wdcp.microsoft.com
23-Jul-2016 14:23:38.204 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0060178 wdcp.microsoft.akadns.net
23-Jul-2016 14:23:38.204 resolver: debug 1: fetch: wdcp.microsoft.akadns.net/A
23-Jul-2016 14:23:38.217 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0060178 wdcp.microsoft.akadns.net
23-Jul-2016 14:23:38.218 resolver: debug 1: fetch: wdcpall.microsoft.akadns.net/A
23-Jul-2016 14:23:38.231 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063940 wdcpall.microsoft.akadns.net
23-Jul-2016 14:23:48.306 resolver: debug 1: fetch: outlook.office365.com/A
23-Jul-2016 14:23:48.306 resolver: debug 1: fetch: ./NS
23-Jul-2016 14:23:48.320 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00601f0 outlook.office365.com
23-Jul-2016 14:23:48.320 database: debug 1: decrement_reference: delete from rbt: 0x7f78b00601f0 lb.geo.office365.com
23-Jul-2016 14:23:48.320 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0067120 outlook.office365.com.g.office365.com
23-Jul-2016 14:23:48.320 resolver: debug 1: fetch: office365.com/DS
23-Jul-2016 14:23:48.334 resolver: debug 1: fetch: lb.geo.office365.com/A
23-Jul-2016 14:23:48.347 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063a90 lb.geo.office365.com
23-Jul-2016 14:23:48.347 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0068510 outlook.office365.com.g.office365.com
23-Jul-2016 14:23:48.347 resolver: debug 1: fetch: outlook.office365.com.g.office365.com/A
23-Jul-2016 14:23:48.360 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0068510 outlook.office365.com.g.office365.com
23-Jul-2016 14:23:48.361 resolver: debug 1: fetch: outlook-au.office365.com/A
23-Jul-2016 14:23:48.373 database: debug 1: decrement_reference: delete from rbt: 0x7f78b0063b00 outlook-au.office365.com

```

Yes I have changed serials on both to 5 - so should I now be able to check that a computers short name is being resolved by DNS with the command dig ubuntuws01 or dig grantlp01 ?

**db.geekhelp.local**
```

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ubuntuws01.lan.geekhelp.co.nz. algrant.local. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ubuntuws01.lan.geekhelp.co.nz.
@       IN      A       127.0.0.1
@       IN      AAAA    ::1

; *** A RECORDS ***

ubuntuws01                      IN      A       192.168.55.254
draytek                         IN      A       192.168.55.1
ubuntuws01.lan.geekhelp.co.nz   IN      A       192.168.55.254
lan.geekhelp.co.nz              IN      A       127.0.0.1

; *** CNAME RECORDS ***
ns                              IN      CNAME   ubuntuws01

```

**db.192**
```

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ubuntuws01.lan.geekhelp.co.nz. algrant.local. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ubuntuws01.lan.geekhelp.co.nz.
1       IN      PTR     draytek.lan.geekhelp.co.nz.
254     IN      PTR     ubuntuws01.lan.geekhelp.co.nz.

```

They look ok?


Cheers

-Al

---

### Post by papibe on 2016-07-22
Both db.geekhelp.local and db.192 have a serial field
```
 4         ; Serial
```
increase the value to force the info to be reloaded:
```
 5         ; Serial
```

---

### Post by Al Grant on 2016-07-22
Yes I saw that once I posted.

Now how can I best check that short hostnames, ie grantws01 or grantlp01 are resolving via a DNS query? 

Cheers

-Al

---

### Post by papibe on 2016-07-22
There are some inconveniences for testing this.

Since the machines that are already in your network have a lease from DHCP, they won't be requesting an update any time soon. Thus, they have been not added to the DNS database.

In order to force it, try turning of WIFI, or plain rebooting a client machine. Once you are sure it requested/renew a new address (watching the logs), you can then try to test both full name, and short name resolution.

Regards.

---

### Post by Al Grant on 2016-07-22
Hmmm, things still not quite right. If on a windows client I issue:

```

C:\Users\bigal>nslookup grantlp01
Server:  UnKnown
Address:  192.168.55.254

Name:    GRANTLP01.lan.geekhelp.co.nz
Address:  192.168.55.103


C:\Users\bigal>

```

It triggers the following on the /var/log/named/bind.log:

```

client 192.168.55.101#49380 (254.55.168.192.in-addr.arpa): query failed (SERVFAIL) for 254.55.168.192.in-addr.arpa/IN/PTR at bin/named/query.c:6477

```

Note I had to edit the end of the above line to get it to paste, but it was PTR at ./././bin

---

### Post by Al Grant on 2016-07-22
Ok I fixed the above error (I needed to modify both zones to file "/var/cache/bind/db.192" etc)

The final problem I seem to now be faced with is reverse lookup.

Some clients on my network I can reverse lookup, for example my phone from a windows client:

```
C:\Users\bigal>nslookup 192.168.55.102
Server:  ubuntuws01.lan.geekhelp.co.nz
Address:  192.168.55.254

Name:    android-30d774ad10e81119.lan.geekhelp.co.nz
Address:  192.168.55.102

```

But I can't lookup one of the windows hosts:

```
 C:\Users\bigal>nslookup 192.168.55.101
Server:  ubuntuws01.lan.geekhelp.co.nz
Address:  192.168.55.254

*** ubuntuws01.lan.geekhelp.co.nz can't find 192.168.55.101: Non-existent domain

```

I noted on the logs that my android phone when I came home did get a reverse map successfully added:

```
 Jul 23 16:45:57 UBUNTUWS01 dhcpd[27334]: DHCPACK on 192.168.55.102 to ec:1f:72:dd:8e:59 (android-30d774ad10e81119) via enp1s0
Jul 23 16:45:57 UBUNTUWS01 dhcpd[27334]: Added new forward map from android-30d774ad10e81119.lan.geekhelp.co.nz. to 192.168.55.102
Jul 23 16:45:57 UBUNTUWS01 dhcpd[27334]: Added reverse map from 102.55.168.192.in-addr.arpa. to android-30d774ad10e81119.lan.geekhelp.co.nz.

```

Any ideas?

Cheers (again)

-Al

---

### Post by papibe on 2016-07-23
Let's check the basics. What settings is getting the Windows machine from DHCP:

Could you run this in your Windows client, and paste back the output?
```
ipconfig /all
```
Then, in your server you can check if that is the correct lease:
```
cat /var/lib/dhcp/dhcpd.leases
```
And then you can check if the client machine's IP is on the DNS server:
```
cat /var/cache/bind/db.geekhelp.local
cat /var/cache/bind/db.192
```
Let us know what you find out.
Regards.

---

### Post by Al Grant on 2016-07-23
As you wish :-)

** ipconfig /all **
```
C:\Users\bigal>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : GRANTWS01
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Mixed
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : lan.geekhelp.co.nz

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : lan.geekhelp.co.nz
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 00-24-8C-FD-FE-1F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::2170:e2a:b0f0:5a38%12(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.55.101(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, 23 July 2016 11:06:13 PM
   Lease Expires . . . . . . . . . . : Saturday, 13 August 2016 2:46:24 PM
   Default Gateway . . . . . . . . . : 192.168.55.1
   DHCP Server . . . . . . . . . . . : 192.168.55.254
   DHCPv6 IAID . . . . . . . . . . . : 50341004
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1F-1C-C0-0F-00-24-8C-FD-FE-1F
   DNS Servers . . . . . . . . . . . : 192.168.55.254
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Ethernet 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : TAP-Windows Adapter V9
   Physical Address. . . . . . . . . : 00-FF-6F-D6-AC-91
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:79fb:0:6ac4:e403:4726(Preferred)
   Link-local IPv6 Address . . . . . : fe80::6ac4:e403:4726%14(Preferred)
   Default Gateway . . . . . . . . . : ::
   DHCPv6 IAID . . . . . . . . . . . : 134217728
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1F-1C-C0-0F-00-24-8C-FD-FE-1F
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.lan.geekhelp.co.nz:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : lan.geekhelp.co.nz
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

C:\Users\bigal>

```

** dhcpd.leases **
```

algrant@ubuntuws01:~$ sudo cat /var/lib/dhcp/dhcpd.leases
[sudo] password for algrant:
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-4.3.3

lease 192.168.55.104 {
  starts 4 2016/07/21 20:00:15;
  ends 4 2016/08/11 20:00:15;
  tstp 4 2016/08/11 20:00:15;
  cltt 5 2016/07/22 20:10:27;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 50:56:bf:38:70:e7;
  uid "\001PV\2778p\347";
  set vendor-class-identifier = "udhcp v1.21.1";
}
lease 192.168.55.105 {
  starts 5 2016/07/22 00:05:38;
  ends 5 2016/08/12 00:05:38;
  tstp 5 2016/08/12 00:05:38;
  cltt 5 2016/07/22 05:08:18;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 5c:8d:4e:e5:37:8a;
  uid "\001\\\215N\3457\212";
}
lease 192.168.55.106 {
  starts 5 2016/07/22 01:46:40;
  ends 5 2016/08/12 01:46:40;
  tstp 5 2016/08/12 01:46:40;
  cltt 5 2016/07/22 01:46:40;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 64:a5:c3:7c:c6:9c;
  uid "\001d\245\303|\306\234";
  client-hostname "Mobi";
}
lease 192.168.55.100 {
  starts 5 2016/07/22 08:59:02;
  ends 5 2016/08/12 08:59:02;
  tstp 5 2016/08/12 08:59:02;
  cltt 5 2016/07/22 08:59:02;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet e8:11:32:db:8c:b4;
  uid "\001\350\0212\333\214\264";
  set vendor-class-identifier = "MSFT 5.0";
  client-hostname "GRANTLP01";
}
lease 192.168.55.103 {
  starts 6 2016/07/23 02:23:22;
  ends 6 2016/08/13 02:23:22;
  tstp 6 2016/08/13 02:23:22;
  cltt 6 2016/07/23 02:23:22;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 40:25:c2:84:3a:cc;
  uid "\001@%\302\204:\314";
  set vendor-class-identifier = "MSFT 5.0";
  set ddns-fwd-name = "GRANTLP01.lan.geekhelp.co.nz.";
  set ddns-txt = "3117c8e57da9ed449ad55e9d4b058726a7";
  client-hostname "GRANTLP01";
}
lease 192.168.55.101 {
  starts 6 2016/07/23 02:46:36;
  ends 6 2016/08/13 02:46:36;
  tstp 6 2016/08/13 02:46:36;
  cltt 6 2016/07/23 11:06:25;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 00:24:8c:fd:fe:1f;
  uid "\001\000$\214\375\376\037";
  set ddns-txt = "31c48d8f5d5dd8e839fc57bd57c657ad5a";
  set ddns-fwd-name = "GRANTWS01.lan.geekhelp.co.nz.";
  set vendor-class-identifier = "MSFT 5.0";
}
lease 192.168.55.102 {
  starts 6 2016/07/23 04:45:57;
  ends 6 2016/08/13 04:45:57;
  tstp 6 2016/08/13 04:45:57;
  cltt 6 2016/07/23 04:45:57;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet ec:1f:72:dd:8e:59;
  uid "\001\354\037r\335\216Y";
  set vendor-class-identifier = "dhcpcd-5.5.6";
  set ddns-fwd-name = "android-30d774ad10e81119.lan.geekhelp.co.nz.";
  set ddns-txt = "3112c76edad70d09e6de54a91ba142fcb9";
  set ddns-rev-name = "102.55.168.192.in-addr.arpa.";
  client-hostname "android-30d774ad10e81119";
}
lease 192.168.55.107 {
  starts 6 2016/07/23 05:15:14;
  ends 6 2016/08/13 05:15:14;
  tstp 6 2016/08/13 05:15:14;
  cltt 6 2016/07/23 05:15:14;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 7c:01:91:85:a1:0e;
  uid "\001|\001\221\205\241\016";
  set ddns-rev-name = "107.55.168.192.in-addr.arpa.";
  set ddns-txt = "31d0cdea2046c52e6501ddf9f7ab1a68e1";
  set ddns-fwd-name = "iphone.lan.geekhelp.co.nz.";
  client-hostname "iphone";
}
lease 192.168.55.109 {
  starts 6 2016/07/23 10:47:48;
  ends 6 2016/08/13 10:47:48;
  tstp 6 2016/08/13 10:47:48;
  cltt 6 2016/07/23 14:46:58;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 34:64:a9:cf:19:2a;
  uid "\0014d\251\317\031*";
  set ddns-rev-name = "109.55.168.192.in-addr.arpa.";
  set ddns-txt = "316224be2b2f6266497a0ee46730db5bc9";
  set ddns-fwd-name = "HPLP01.lan.geekhelp.co.nz.";
  set vendor-class-identifier = "MSFT 5.0";
}
lease 192.168.55.108 {
  starts 6 2016/07/23 19:45:08;
  ends 6 2016/08/13 19:45:08;
  cltt 6 2016/07/23 19:45:08;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet f8:16:54:a8:77:cb;
  uid "\001\370\026T\250w\313";
  set ddns-rev-name = "108.55.168.192.in-addr.arpa.";
  set ddns-txt = "31e3f959162c1803bb5a6da89608fafc64";
  set ddns-fwd-name = "DESKTOP-RB3MJLV.lan.geekhelp.co.nz.";
  set vendor-class-identifier = "MSFT 5.0";
  client-hostname "HPLP01";
}
lease 192.168.55.108 {
  starts 6 2016/07/23 19:45:08;
  ends 6 2016/08/13 19:45:08;
  cltt 6 2016/07/23 19:45:08;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet f8:16:54:a8:77:cb;
  uid "\001\370\026T\250w\313";
  set ddns-rev-name = "108.55.168.192.in-addr.arpa.";
  set vendor-class-identifier = "MSFT 5.0";
  client-hostname "HPLP01";
}
lease 192.168.55.108 {
  starts 6 2016/07/23 19:45:08;
  ends 6 2016/08/13 19:45:08;
  cltt 6 2016/07/23 19:45:08;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet f8:16:54:a8:77:cb;
  uid "\001\370\026T\250w\313";
  set vendor-class-identifier = "MSFT 5.0";
  client-hostname "HPLP01";
}
lease 192.168.55.108 {
  starts 6 2016/07/23 20:13:26;
  ends 6 2016/08/13 20:13:26;
  cltt 6 2016/07/23 20:13:26;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet f8:16:54:a8:77:cb;
  uid "\001\370\026T\250w\313";
  set vendor-class-identifier = "MSFT 5.0";
  client-hostname "HPLP01";
}
algrant@ubuntuws01:~$

```

**db.geekhelp.local**
```

algrant@ubuntuws01:~$ sudo cat /var/cache/bind/db.geekhelp.local
$ORIGIN .
$TTL 604800     ; 1 week
lan.geekhelp.co.nz      IN SOA  ubuntuws01.lan.geekhelp.co.nz. algrant.local. (
                                21         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      ubuntuws01.lan.geekhelp.co.nz.
                        A       127.0.0.1
                        AAAA    ::1
$ORIGIN lan.geekhelp.co.nz.
$TTL 3600       ; 1 hour
android-30d774ad10e81119 A      192.168.55.102
                        TXT     "3112c76edad70d09e6de54a91ba142fcb9"
$TTL 604800     ; 1 week
draytek                 A       192.168.55.1
$TTL 3600       ; 1 hour
GRANTLP01               A       192.168.55.103
                        TXT     "3117c8e57da9ed449ad55e9d4b058726a7"
GRANTWS01               A       192.168.55.101
                        TXT     "31c48d8f5d5dd8e839fc57bd57c657ad5a"
$TTL 604800     ; 1 week
ns                      CNAME   ubuntuws01
lan.geekhelp.co.nz      A       127.0.0.1
$ORIGIN lan.geekhelp.co.nz.lan.geekhelp.co.nz.
ubuntuws01              A       192.168.55.254
$ORIGIN lan.geekhelp.co.nz.
$TTL 3600       ; 1 hour
HPLP01           A       192.168.55.109
                        TXT     "316224be2b2f6266497a0ee46730db5bc9"
iphone           A       192.168.55.107
                        TXT     "31d0cdea2046c52e6501ddf9f7ab1a68e1"
$TTL 604800     ; 1 week
ubuntuws01              A       192.168.55.254
algrant@ubuntuws01:~$

```

**db.192**
```

algrant@ubuntuws01:~$ sudo cat /var/cache/bind/db.192
$ORIGIN .
$TTL 604800     ; 1 week
55.168.192.in-addr.arpa IN SOA  ubuntuws01.lan.geekhelp.co.nz. algrant.local. (
                                12         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      ubuntuws01.lan.geekhelp.co.nz.
$ORIGIN 55.168.192.in-addr.arpa.
1                       PTR     draytek.lan.geekhelp.co.nz.
$TTL 3600       ; 1 hour
102                     PTR     android-30d774ad10e81119.lan.geekhelp.co.nz.
107                     PTR     iphone.lan.geekhelp.co.nz.
109                     PTR     HPLP01.lan.geekhelp.co.nz.
$TTL 604800     ; 1 week
254                     PTR     ubuntuws01.lan.geekhelp.co.nz.
algrant@ubuntuws01:~$

```


I see it looks like some devices are missing from the reverse lookup?

Cheers again

-Al

---

### Post by papibe on 2016-07-24
I think it's working.

The problem right now may be coming from a previous configuration that was partially working. If everything is fine, all resolution problems will resolve itself.

It would be interesting to test with a new device. An unused tablet, an old computer. This way it would have a fresh run with dhcp and dns. If the new device name can be resolve from the other devices, we're golden.

A success would mean that is resolving:
[LIST]
[*]shortnames,
[*]long names with the local domain, and
[*]reverse lookups
[/LIST]
Let us know if you can do that test, and its results.
Regards.

---

### Post by Al Grant on 2016-07-24
What about winding down the lease time to say 30 minutes? Would that fix everything pretty quick?

I don't really have any more laptops :-)

Regards

-Al

---

### Post by Al Grant on 2016-07-24
Ok, I went ahead and dialed down the lease time:

On a windows client (grantws01) I was able to resolve (for:
    * resolve short-name (grantws01)
    * resolve long name (grantws01.lan.geekhelp.co.nz)
    * reverse look ups (192.168.55.101)

Also on grantws01 I was able to do forward and reverse lookups for ubuntuws01.

I went to do the same on the ubuntuws01 with dig and was able to dig ubuntuws01.lan.geekhelp.co.nz but was not able to dig short-name ubuntuws01. Is this because dig doesn't automatically append prefixes but nslookup does? (nslookup ubuntuws01 of course did work....)

I have remembered that ubuntuws01 is actually (and logically) assigned a static IP. (nmcli connection show 'Wired connection 1' ipv4.method = manual).

I think all is good. Could I be sure host name resolution is done by looking at wireshark during a ping <shortname>

Cheers 

-Al

---

### Post by Al Grant on 2016-07-26
Thanks papibe for all your help !!

I am marking this as solved.

Cheers

-Al

---

### Post by papibe on 2016-07-26
> **Al Grant said:**
> I have remembered that ubuntuws01 is actually (and logically) assigned a static IP. (nmcli connection show 'Wired connection 1' ipv4.method = manual).
If you need a machine to have an static IP, you can set it up with a reservation on the DHCP server.  Add something like this to your /etc/dhcp/dhcpd.conf
```
subnet ... {

  host cliente_hostname {
    hardware ethernet 00:11:25:f7:54:15;
    fixed-address 192.168.55.2;

  }
...

```
Restart the dhcpd service and then turn the client machine back to 'Automatic (DHCP)' on the network manager.

I understand that ubuntuws01 _is_ the dhcp/dns server so this case is different. It should have an static IP. However, in order for the name ubuntuws01 to be resolve you need to manually create entries in your db.geekhelp.local:
```
...
ubuntuws01                      IN      A       192.168.55.254
...
```
and dp.192:
```
...
254     IN      PTR     ubuntuws01.lan.geekhelp.co.nz.
...
```
For what I can see, you already have that, but also have other entries that may be confusing. I'd get rid off:
```
lan.geekhelp.co.nz      A       127.0.0.1
```
and leave just one of these (there are two at the moment):
```
ubuntuws01                      IN      A       192.168.55.254
```
Stop the bind service, edit the files, increase the serial, and start the service.

Hope that helps. Let us know how it goes.
Regards.

---

