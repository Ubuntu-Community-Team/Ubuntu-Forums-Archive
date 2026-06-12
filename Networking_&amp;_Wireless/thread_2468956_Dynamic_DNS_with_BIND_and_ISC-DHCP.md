---
title: "Dynamic DNS with BIND and ISC-DHCP"
date: 2021-11-15
forum: Networking &amp; Wireless
---

### Post by tycoon186 on 2021-11-15
Good afternoon.
The DHCP server cannot update the zone file.
Zone log files do not appear in / var / lib / bind.
Please tell me what I'm doing wrong.


Ubuntu server 20.04
IP server dns and dhcp: 172.26.15.17
Gateway: 172.26.15.1
Hostname server: ddns
Purpose: to configure a dynamically updated DNS server for the local network.


**Log dhcp:** 
Nov 15 17:30:54 ddns dhcpd[683]: Sending on   Socket/fallback/fallback-net
Nov 15 17:30:54 ddns dhcpd[683]: Can't create PID file /run/dhcp-server/dhcpd.pid: No such file or directory.
Nov 15 17:30:54 ddns dhcpd[683]: Server starting service.
Nov 15 17:57:01 ddns dhcpd[683]: DHCPREQUEST for 172.26.15.24 from 08:00:27:cb:1e:43 via enp0s3: unknown lease 172.26.15.24.
Nov 15 18:00:24 ddns dhcpd[683]: DHCPREQUEST for 172.26.15.24 from 08:00:27:cb:1e:43 via enp0s3: unknown lease 172.26.15.24.
Nov 15 18:00:26 ddns dhcpd[683]: DHCPDISCOVER from 08:00:27:cb:1e:43 via enp0s3
Nov 15 18:00:27 ddns dhcpd[683]: DHCPOFFER on 172.26.15.103 to 08:00:27:cb:1e:43 (test01) via enp0s3
Nov 15 18:00:27 ddns dhcpd[683]: DHCPREQUEST for 172.26.15.103 (172.26.15.17) from 08:00:27:cb:1e:43 (test01) via enp0s3
Nov 15 18:00:27 ddns dhcpd[683]: DHCPACK on 172.26.15.103 to 08:00:27:cb:1e:43 (test01) via enp0s3
Nov 15 18:00:27 ddns dhcpd[683]: **Unable to add forward map from test01.LAB.LOCAL to 172.26.15.103: REFUSED**

[B]Log bind:
[/B]Nov 15 17:30:56 ddns named[687]: zone 15.26.172.in-addr.arpa/IN: loaded serial 2
Nov 15 17:30:56 ddns named[687]: zone localhost/IN: loaded serial 2
Nov 15 17:30:56 ddns named[687]: zone 127.in-addr.arpa/IN: loaded serial 1
Nov 15 17:30:56 ddns named[687]: zone LAB.LOCAL/IN: loaded serial 2
Nov 15 17:30:56 ddns named[687]: zone 255.in-addr.arpa/IN: loaded serial 1
Nov 15 17:30:56 ddns named[687]: all zones loaded
Nov 15 17:30:56 ddns named[687]: running
Nov 15 17:30:56 ddns named[687]: managed-keys-zone: Key 20326 for zone . is now trusted (acceptance timer complete)
Nov 15 17:30:57 ddns named[687]: resolver priming query complete
Nov 15 18:00:27 ddns named[687]: **client @0x7fd4180228b0 172.26.15.17#40487/key dhcp_updater: update 'LAB.LOCAL/IN' denied**



[B]
Configure isc-dhcp-server[/B]
/etc/dhcp/dhcpd.conf
```

default-lease-time 600;
max-lease-time 7200;
ddns-updates on;
ddns-update-style interim;
update-static-leases on;
authoritative;


key DHCP_UPDATER {
        algorithm HMAC-MD5;
        secret "zeR6EAytjI4bhleeKj9Xbg==";
        }


zone LAB.LOCAL {
        primary 172.26.15.17;
        key DHCP_UPDATER;
        }


zone 15.26.172.in-addr.arpa. {
        primary 172.26.15.17;
        key DHCP_UPDATER;
        }


subnet 172.26.15.0 netmask 255.255.255.0 {
        interface enp0s3;
        range 172.26.15.100 172.26.15.120;
        option domain-name  "LAB.LOCAL";
        option domain-name-servers 172.26.15.17;
        option routers 172.26.15.1;
        option broadcast-address 172.26.15.255;
}
log-facility local7;

```

/etc/default/isc-dhcp-server
```

INTERFACESv4="enp0s3"
INTERFACESv6=""

```

/etc/resolv.conf
```

nameserver 172.26.15.17
search LAB.LOCAL

```



**Configure Bind9**
/etc/bind/named.conf.options
```
options {
        directory "/var/cache/bind";


        forwarders {
                8.8.8.8;
                8.8.4.4;
        };


        listen-on {
        127.0.0.1;
        172.26.15.17;
        };


        dnssec-validation auto;
};

```

**Live view area**
/var/lib/bind/forward.bind
```

$TTL    604800
@       IN      SOA     ddns.LAB.LOCAL. root.ddns.LAB.LOCAL. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ddns.LAB.LOCAL.
@       IN      A       172.26.15.17


ddns   IN      A       172.26.15.17
test    IN      A       172.26.15.20

```

[B]Reverse lookup zone
[/B]/var/lib/bind/reverse.bind
```

$TTL    604800
@       IN      SOA     ddns.LAB.LOCAL. root.ddns.LAB.LOCAL. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ddns.LAB.LOCAL.
17      IN      PTR     ddns.LAB.LOCAL.
20      IN      PTR     test.LAB.LOCAL.

```


/etc/bind/named.conf.local
```

key DHCP_UPDATER {
        algorithm HMAC-MD5.SIG-ALG.REG.INT;
        secret "zeR6EAytjI4bhleeKj9Xbg==";
        };


zone "LAB.LOCAL" {
        type master;
        file "/var/lib/bind/forward.bind";
        };


zone "15.26.172.in-addr.arpa" {
        type master;
        file "/var/lib/bind/reverse.bind";
        };

```

---

