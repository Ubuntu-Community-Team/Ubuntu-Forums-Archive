---
title: "BIND9 views runs, but does not respond to DNS queries"
date: 2014-12-02
forum: Networking &amp; Wireless
---

### Post by happyraver1958-9 on 2014-12-02
**Symptoms:**
My BIND9 server will read the configuration files, run the daemon as expected, no significant errors in the error log (I fixed all the ones that popped up) and everything runs fine; as long as there are no views in the configuration files.  Once there are views involved, the server stops responding to DNS queries altogether.
It works just fine when there's a configuration that doesn't use views; this only happens when views are used.

I've used dig and nslookup, from within the server and outside the server, they all respond with SERVFAIL status as follows:

```
[FONT=courier new]root@DNSSERVER:/bindtest# dig @localhost hostname.example.com[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]; <<>> DiG 9.9.5-3-Ubuntu <<>> @localhost hostname.example.com[/FONT]
[FONT=courier new]; (2 servers found)[/FONT]
[FONT=courier new];; global options: +cmd[/FONT]
[FONT=courier new];; Got answer:[/FONT]
[FONT=courier new];; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 9974[/FONT]
[FONT=courier new];; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new];; OPT PSEUDOSECTION:[/FONT]
[FONT=courier new]; EDNS: version: 0, flags:; udp: 4096[/FONT]
[FONT=courier new];; QUESTION SECTION:[/FONT]
[FONT=courier new];hostname.example.com.               IN      A[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new];; Query time: 4000 msec[/FONT]
[FONT=courier new];; SERVER: 127.0.0.1#53(127.0.0.1)[/FONT]
[FONT=courier new];; WHEN: Tue Dec 02 16:44:20 CST 2014[/FONT]
[FONT=courier new];; MSG SIZE  rcvd: 44[/FONT]

```

The same results will occur if I use the server's local IP address instead of @localhost.

The same results from outside the server:

```

[FONT=courier new]Z:\>dig @192.168.151.25 hostname.example.com[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]; <<>> DiG 9.9.6 <<>> @192.168.151.25 hostname.example.com[/FONT]
[FONT=courier new]; (1 server found)[/FONT]
[FONT=courier new];; global options: +cmd[/FONT]
[FONT=courier new];; connection timed out; no servers could be reached
[/FONT]
```

And from another server within the same subnet:

```

[FONT=courier new][root@server2 ~]# dig @192.168.151.25 hostname.example.com[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]; <<>> DiG 9.9.3-rl.156.01-P1-RedHat-9.9.3-3.P1.fc18 <<>> @192.168.151.25 hostname.example.com[/FONT]
[FONT=courier new]; (1 server found)[/FONT]
[FONT=courier new];; global options: +cmd[/FONT]
[FONT=courier new];; Got answer:[/FONT]
[FONT=courier new];; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 60499[/FONT]
[FONT=courier new];; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new];; OPT PSEUDOSECTION:[/FONT]
[FONT=courier new]; EDNS: version: 0, flags:; udp: 4096[/FONT]
[FONT=courier new];; QUESTION SECTION:[/FONT]
[FONT=courier new];hostname.example.com.               IN      A[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new];; Query time: 0 msec[/FONT]
[FONT=courier new];; SERVER: 192.168.151.25#53(192.168.151.25)[/FONT]
[FONT=courier new];; WHEN: Tue Dec 02 16:47:29 CST 2014[/FONT]
[FONT=courier new];; MSG SIZE  rcvd: 44[/FONT]

```



**Here's the test configuration files I'm using:**

named.conf:
```

[FONT=courier new]include "/bindtest/named.conf.options";[/FONT]
[FONT=courier new]include "/bindtest/named.conf.local";[/FONT]
[FONT=courier new]include "/bindtest/named.conf.default-zones";[/FONT]

```

named.conf.options:
```

[FONT=courier new]options {[/FONT]
[FONT=courier new]    directory "/var/cache/bind";[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    // If there is a firewall between you and nameservers you want[/FONT]
[FONT=courier new]    // to talk to, you may need to fix the firewall to allow multiple[/FONT]
[FONT=courier new]    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    // If your ISP provided one or more IP addresses for stable [/FONT]
[FONT=courier new]    // nameservers, you probably want to use them as forwarders.  [/FONT]
[FONT=courier new]    // Uncomment the following block, and insert the addresses replacing [/FONT]
[FONT=courier new]    // the all-0's placeholder.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    // forwarders {[/FONT]
[FONT=courier new]    //     0.0.0.0;[/FONT]
[FONT=courier new]    // };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    //========================================================================[/FONT]
[FONT=courier new]    // If BIND logs error messages about the root key being expired,[/FONT]
[FONT=courier new]    // you will need to update your keys.  See https://www.isc.org/bind-keys[/FONT]
[FONT=courier new]    //========================================================================[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    auth-nxdomain no;    # conform to RFC1035[/FONT]
[FONT=courier new]    // listen-on-v6 { any; };[/FONT]
[FONT=courier new]    listen-on {  any;  };[/FONT]
[FONT=courier new]};[/FONT]

```

named.conf.local:
```

[FONT=courier new]include "/bindtest/zones.rfc1918";[/FONT]
[FONT=courier new]include "/bindtest/zones.example.com";
[/FONT]
```

named.conf.default-zones:
```

[FONT=courier new]view "default-zones"  {[/FONT]
[FONT=courier new]    match-clients  {  any;  };   // Everything will match[/FONT]
[FONT=courier new]    // prime the server with knowledge of the root servers[/FONT]
[FONT=courier new]    zone "." {[/FONT]
[FONT=courier new]        type hint;[/FONT]
[FONT=courier new]        file "/etc/bind/db.root";[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    // be authoritative for the localhost forward and reverse zones, and for[/FONT]
[FONT=courier new]    // broadcast zones as per RFC 1912[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "localhost" {[/FONT]
[FONT=courier new]        type master;[/FONT]
[FONT=courier new]        file "/etc/bind/db.local";[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "127.in-addr.arpa" {[/FONT]
[FONT=courier new]        type master;[/FONT]
[FONT=courier new]        file "/etc/bind/db.127";[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "0.in-addr.arpa" {[/FONT]
[FONT=courier new]        type master;[/FONT]
[FONT=courier new]        file "/etc/bind/db.0";[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "255.in-addr.arpa" {[/FONT]
[FONT=courier new]        type master;[/FONT]
[FONT=courier new]        file "/etc/bind/db.255";[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]};[/FONT]

```

zones.example.com:
```

[FONT=courier new]
[/FONT]
[FONT=courier new]// be authoritative for the localhost forward and reverse zones, and for[/FONT]
[FONT=courier new]// broadcast zones as per RFC 1912[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]view "reverse-lookup"  {[/FONT]
[FONT=courier new]    match-clients  {  any;  };[/FONT]
[FONT=courier new]    match-destinations  {  any;  };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "150.168.192.in-addr.arpa"  IN  {[/FONT]
[FONT=courier new]        type master;[/FONT]
[FONT=courier new]        file "/bindtest/150.168.192.in-addr.arpa";[/FONT]
[FONT=courier new]        allow-update  {  none;  };[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "151.168.192.in-addr.arpa"  IN  {[/FONT]
[FONT=courier new]        type master;[/FONT]
[FONT=courier new]        file "/bindtest/151.168.192.in-addr.arpa";[/FONT]
[FONT=courier new]        allow-update  {  none;  };[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]};[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]view "internal"  {[/FONT]
[FONT=courier new]    match-clients  {  192.168/16;  };[/FONT]
[FONT=courier new]    match-destinations  {  192.168/16;  };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    recursion yes;[/FONT]
[FONT=courier new]    [/FONT]
[FONT=courier new]    zone "example.com" IN  {[/FONT]
[FONT=courier new]        type master;[/FONT]
[FONT=courier new]        file "/bindtest/internal.example.com";[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]};[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]view "external"  {[/FONT]
[FONT=courier new]    match-clients  {  any;  };[/FONT]
[FONT=courier new]    match-destinations  {  any;  };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    recursion no;[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "example.com" IN  {[/FONT]
[FONT=courier new]        type master;[/FONT]
[FONT=courier new]        file "/bindtest/external.example.com";[/FONT]
[FONT=courier new]    };[/FONT]
[FONT=courier new]};[/FONT]

```





zones.rfc1918:
```

[FONT=courier new]view "reverse-addresses" IN  {[/FONT]
[FONT=courier new]    match-clients  {  any;  };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "10.in-addr.arpa"      { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "16.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "17.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "18.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "19.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "20.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "21.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "22.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "23.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "24.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "25.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "26.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "27.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "28.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "29.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "30.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]    zone "31.172.in-addr.arpa"  { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]    zone "168.192.in-addr.arpa" { type master; file "/bindtest/db.empty"; };[/FONT]
[FONT=courier new]};[/FONT]

```

internal.example.com:
```

[FONT=courier new];  Zone file for example.com.[/FONT]
[FONT=courier new]$TTL    1D[/FONT]
[FONT=courier new]$ORIGIN example.com.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]@    1D    IN    SOA    ns1.example.com.    hostmaster.example.com.  ([/FONT]
[FONT=courier new]                14120102    ; serial[/FONT]
[FONT=courier new]                3h        ; refresh[/FONT]
[FONT=courier new]                15        ; retry[/FONT]
[FONT=courier new]                1w        ; expire[/FONT]
[FONT=courier new]                3h        ; minimum[/FONT]
[FONT=courier new]                )[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]@    IN    NS    ns1.example.com.    ; domain[/FONT]
[FONT=courier new]@    IN    NS    ns2.example.com.    ; secondary[/FONT]
[FONT=courier new]@    IN    MX    10    mail.external-example.com.    ; external mail provider[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]; host server definitions[/FONT]
[FONT=courier new]ns1    IN    A    192.168.151.25        ; this server[/FONT]
[FONT=courier new]ns2    IN    A    192.168.151.25        ; secondary, same server[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]; non-server hosts definitions[/FONT]
[FONT=courier new]zac    IN    A    192.168.150.114[/FONT]
[FONT=courier new]gw    IN    A    192.168.150.22[/FONT]

```



external.example.com:
```

[FONT=courier new];  Zone file for example.com. public domain[/FONT]
[FONT=courier new]$TTL    1D[/FONT]
[FONT=courier new]$ORIGIN example.com.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]@    1D    IN    SOA    ns1.example.com.    hostmaster.example.com.  ([/FONT]
[FONT=courier new]                14120103    ; serial[/FONT]
[FONT=courier new]                3h        ; refresh[/FONT]
[FONT=courier new]                15        ; retry[/FONT]
[FONT=courier new]                1w        ; expire[/FONT]
[FONT=courier new]                3h        ; minimum[/FONT]
[FONT=courier new]                )[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]@    IN    NS    ns1.example.com.    ; domain[/FONT]
[FONT=courier new]@    IN    MX    10    mail.external-example.com.    ; external mail provider[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]; host server definitions[/FONT]
[FONT=courier new]ns1    IN    A    x.x.x.162        ; this server[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]; non-server hosts definitions[/FONT]
[FONT=courier new]zac    IN    A    x.x.x.160[/FONT]
[FONT=courier new]gw    IN    A    x.x.x.161[/FONT]

```

Server and software specs:

Server runs on vmware ESXi 5.5 hypervisor.

**Server version:**
```

[FONT=courier new]NAME="Ubuntu"[/FONT]
[FONT=courier new]VERSION="14.04.1 LTS, Trusty Tahr"[/FONT]
[FONT=courier new]ID=ubuntu[/FONT]
[FONT=courier new]ID_LIKE=debian[/FONT]
[FONT=courier new]PRETTY_NAME="Ubuntu 14.04.1 LTS"[/FONT]
[FONT=courier new]VERSION_ID="14.04"[/FONT]
[FONT=courier new]HOME_URL="http://www.ubuntu.com/"[/FONT]
[FONT=courier new]SUPPORT_URL="http://help.ubuntu.com/"[/FONT]
[FONT=courier new]BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
[/FONT]
```



**BIND9 version:**
```

[FONT=courier new]Package: bind9[/FONT]
[FONT=courier new]Versions:[/FONT]
[FONT=courier new]1:9.9.5.dfsg-3 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages) (/var/lib/dpkg/status)[/FONT]
[FONT=courier new] Description Language:[/FONT]
[FONT=courier new]                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages[/FONT]
[FONT=courier new]                  MD5: afd61d02df1ec6f856b928dfbf6fd201[/FONT]
[FONT=courier new] Description Language: en[/FONT]
[FONT=courier new]                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en[/FONT]
[FONT=courier new]                  MD5: afd61d02df1ec6f856b928dfbf6fd201[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Reverse Depends:[/FONT]
[FONT=courier new]  samba,bind9[/FONT]
[FONT=courier new]  samba,bind9 1:9.5.1[/FONT]
[FONT=courier new]  maas-dns,bind9[/FONT]
[FONT=courier new]  dnsutils:i386,bind9 1:9.1.0-3[/FONT]
[FONT=courier new]  bind9utils:i386,bind9 1:9.9.5.dfsg-1[/FONT]
[FONT=courier new]  bind9:i386,bind9[/FONT]
[FONT=courier new]  zentyal-dns,bind9[/FONT]
[FONT=courier new]  ldap2zone,bind9[/FONT]
[FONT=courier new]  ldap2dns,bind9[/FONT]
[FONT=courier new]  ikiwiki-hosting-dns,bind9[/FONT]
[FONT=courier new]  gadmin-bind,bind9 9.3.2[/FONT]
[FONT=courier new]  dnssec-tools,bind9[/FONT]
[FONT=courier new]  dlz-ldap-enum,bind9[/FONT]
[FONT=courier new]  dhis-tools-dns,bind9[/FONT]
[FONT=courier new]  dhis-dns-engine,bind9[/FONT]
[FONT=courier new]  collectd-core,bind9[/FONT]
[FONT=courier new]  cobbler,bind9[/FONT]
[FONT=courier new]  bindgraph,bind9[/FONT]
[FONT=courier new]  autodns-dhcp,bind9[/FONT]
[FONT=courier new]  samba,bind9[/FONT]
[FONT=courier new]  samba,bind9 1:9.5.1[/FONT]
[FONT=courier new]  maas-dns,bind9[/FONT]
[FONT=courier new]  dnsutils,bind9 1:9.1.0-3[/FONT]
[FONT=courier new]  bind9utils,bind9 1:9.9.5.dfsg-1[/FONT]
[FONT=courier new]Dependencies:[/FONT]
[FONT=courier new]1:9.9.5.dfsg-3 - libbind9-90 (5 1:9.9.5.dfsg-3) libc6 (2 2.14) libcap2 (2 2.10) libdns100 (5 1:9.9.5.dfsg-3) libisc95 (5 1:9.9.5.d[/FONT]
[FONT=courier new]fsg-3) libisccc90 (5 1:9.9.5.dfsg-3) libisccfg90 (5 1:9.9.5.dfsg-3) liblwres90 (5 1:9.9.5.dfsg-3) libxml2 (2 2.7.4) debconf (18 0.[/FONT]
[FONT=courier new]5) debconf-2.0 (0 (null)) init-system-helpers (2 1.13~) netbase (0 (null)) adduser (0 (null)) lsb-base (2 3.2-14) bind9utils (5 1:[/FONT]
[FONT=courier new]9.9.5.dfsg-3) net-tools (0 (null)) dnsutils (0 (null)) bind9-doc (0 (null)) resolvconf (0 (null)) ufw (0 (null)) apparmor-profiles[/FONT]
[FONT=courier new] (3 2.1+1075-0ubuntu4) apparmor-profiles:i386 (3 2.1+1075-0ubuntu4) bind (0 (null)) bind:i386 (0 (null)) apparmor-profiles (3 2.1+[/FONT]
[FONT=courier new]1075-0ubuntu4) apparmor-profiles:i386 (3 2.1+1075-0ubuntu4) bind (0 (null)) bind:i386 (0 (null)) bind9utils (3 1:9.9.3.dfsg.P2-3)[/FONT]
[FONT=courier new]bind9utils:i386 (3 1:9.9.3.dfsg.P2-3) dnsutils (3 1:9.1.0-3) dnsutils:i386 (3 1:9.1.0-3) bind9:i386 (0 (null))[/FONT]
[FONT=courier new]Provides:[/FONT]
[FONT=courier new]1:9.9.5.dfsg-3 -[/FONT]
[FONT=courier new]Reverse Provides:
[/FONT]
```

**Log file after fresh restart:**
```

Dec  2 17:39:48 DNS2 named[6421]: received control channel command 'stop -p'
Dec  2 17:39:48 DNS2 named[6421]: shutting down: flushing changes
Dec  2 17:39:48 DNS2 named[6421]: stopping command channel on 127.0.0.1#953
Dec  2 17:39:48 DNS2 named[6421]: no longer listening on 127.0.0.1#53
Dec  2 17:39:48 DNS2 named[6421]: no longer listening on 192.168.151.25#53
Dec  2 17:39:48 DNS2 named[6421]: exiting
Dec  2 17:39:49 DNS2 named[7773]: starting BIND 9.9.5-3-Ubuntu -4 -u bind -c /bindtest/named.conf
Dec  2 17:39:49 DNS2 named[7773]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--with-atf=no' '--enable-ipv6' '--enable-rrl' '--enable-filter-aaaa' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2'
Dec  2 17:39:49 DNS2 named[7773]: ----------------------------------------------------
Dec  2 17:39:49 DNS2 named[7773]: BIND 9 is maintained by Internet Systems Consortium,
Dec  2 17:39:49 DNS2 named[7773]: Inc. (ISC), a non-profit 501(c)(3) public-benefit 
Dec  2 17:39:49 DNS2 named[7773]: corporation.  Support and training for BIND 9 are 
Dec  2 17:39:49 DNS2 named[7773]: available at https://www.isc.org/support
Dec  2 17:39:49 DNS2 named[7773]: ----------------------------------------------------
Dec  2 17:39:49 DNS2 named[7773]: adjusted limit on open files from 4096 to 1048576
Dec  2 17:39:49 DNS2 named[7773]: found 1 CPU, using 1 worker thread
Dec  2 17:39:49 DNS2 named[7773]: using 1 UDP listener per interface
Dec  2 17:39:49 DNS2 named[7773]: using up to 4096 sockets
Dec  2 17:39:49 DNS2 named[7773]: loading configuration from '/bindtest/named.conf'
Dec  2 17:39:49 DNS2 named[7773]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Dec  2 17:39:49 DNS2 named[7773]: using default UDP/IPv4 port range: [1024, 65535]
Dec  2 17:39:49 DNS2 named[7773]: using default UDP/IPv6 port range: [1024, 65535]
Dec  2 17:39:49 DNS2 named[7773]: no IPv6 interfaces found
Dec  2 17:39:49 DNS2 named[7773]: listening on IPv4 interface lo, 127.0.0.1#53
Dec  2 17:39:49 DNS2 named[7773]: listening on IPv4 interface eth0, 192.168.151.25#53
Dec  2 17:39:49 DNS2 named[7773]: generating session key for dynamic DNS
Dec  2 17:39:49 DNS2 named[7773]: sizing zone task pool based on 27 zones
Dec  2 17:39:49 DNS2 named[7773]: set up managed keys zone for view reverse-addresses, file 'dc452ee76f730707a26bafc5018ec5f7740cf6384ebfa8689b45ed022dd794cd.mkeys'
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 64.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 65.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 66.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 67.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 68.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 69.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 70.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 71.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 72.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 73.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 74.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 75.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 76.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 77.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 78.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 79.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 80.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 81.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 82.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 83.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 84.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 85.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 86.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 87.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 88.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 89.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 90.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 91.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 92.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 93.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 94.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 95.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 96.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 97.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 98.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 99.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 100.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 101.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 102.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 103.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 104.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 105.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 106.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 107.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 108.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 109.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 110.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 111.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 112.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 113.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 114.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 115.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 116.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 117.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 118.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 119.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 120.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 121.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 122.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 123.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 124.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 125.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 126.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 127.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 0.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 127.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 254.169.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 2.0.192.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 100.51.198.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 113.0.203.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 255.255.255.255.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: D.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 8.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 9.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: A.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: B.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-addresses: 8.B.D.0.1.0.0.2.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: set up managed keys zone for view reverse-lookup, file 'bb2a2af1d2522d8aee85a5f4f643090771ed2ee6705ba8901c3e3d8046e94b85.mkeys'
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 10.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 16.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 17.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 18.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 19.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 20.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 21.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 22.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 23.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 24.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 25.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 26.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 27.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 28.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 29.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 30.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 31.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 168.192.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 64.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 65.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 66.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 67.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 68.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 69.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 70.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 71.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 72.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 73.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 74.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 75.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 76.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 77.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 78.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 79.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 80.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 81.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 82.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 83.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 84.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 85.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 86.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 87.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 88.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 89.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 90.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 91.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 92.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 93.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 94.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 95.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 96.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 97.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 98.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 99.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 100.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 101.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 102.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 103.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 104.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 105.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 106.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 107.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 108.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 109.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 110.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 111.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 112.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 113.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 114.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 115.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 116.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 117.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 118.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 119.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 120.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 121.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 122.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 123.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 124.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 125.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 126.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 127.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 0.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 127.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 254.169.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 2.0.192.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 100.51.198.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 113.0.203.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 255.255.255.255.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: D.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 8.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 9.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: A.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: B.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view reverse-lookup: 8.B.D.0.1.0.0.2.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: set up managed keys zone for view internal, file '3bed2cb3a3acf7b6a8ef408420cc682d5520e26976d354254f528c965612054f.mkeys'
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 10.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 16.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 17.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 18.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 19.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 20.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 21.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 22.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 23.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 24.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 25.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 26.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 27.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 28.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 29.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 30.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 31.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 168.192.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 64.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 65.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 66.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 67.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 68.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 69.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 70.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 71.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 72.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 73.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 74.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 75.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 76.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 77.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 78.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 79.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 80.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 81.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 82.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 83.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 84.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 85.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 86.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 87.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 88.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 89.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 90.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 91.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 92.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 93.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 94.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 95.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 96.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 97.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 98.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 99.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 100.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 101.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 102.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 103.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 104.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 105.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 106.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 107.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 108.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 109.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 110.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 111.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 112.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 113.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 114.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 115.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 116.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 117.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 118.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 119.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 120.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 121.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 122.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 123.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 124.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 125.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 126.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 127.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 0.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 127.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 254.169.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 2.0.192.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 100.51.198.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 113.0.203.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 255.255.255.255.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: D.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 8.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 9.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: A.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: B.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view internal: 8.B.D.0.1.0.0.2.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: set up managed keys zone for view external, file '3c4623849a49a53911c4a3e48d8cead8a1858960bccdea7a1b978d73ec2f06d7.mkeys'
Dec  2 17:39:49 DNS2 named[7773]: set up managed keys zone for view default-zones, file '570424674be3bdc9fb89a7cbd63a36de811b98f49f4fe80e4eb45cc032be4385.mkeys'
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 10.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 16.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 17.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 18.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 19.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 20.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 21.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 22.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 23.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 24.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 25.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 26.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 27.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 28.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 29.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 30.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 31.172.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 168.192.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 64.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 65.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 66.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 67.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 68.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 69.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 70.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 71.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 72.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 73.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 74.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 75.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 76.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 77.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 78.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 79.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 80.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 81.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 82.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 83.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 84.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 85.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 86.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 87.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 88.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 89.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 90.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 91.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 92.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 93.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 94.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 95.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 96.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 97.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 98.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 99.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 100.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 101.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 102.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 103.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 104.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 105.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 106.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 107.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 108.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 109.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 110.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 111.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 112.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 113.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 114.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 115.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 116.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 117.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 118.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 119.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 120.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 121.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 122.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 123.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 124.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 125.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 126.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 127.100.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 254.169.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 2.0.192.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 100.51.198.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 113.0.203.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 255.255.255.255.IN-ADDR.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: D.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 8.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 9.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: A.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: B.E.F.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: automatic empty zone: view default-zones: 8.B.D.0.1.0.0.2.IP6.ARPA
Dec  2 17:39:49 DNS2 named[7773]: command channel listening on 127.0.0.1#953
Dec  2 17:39:49 DNS2 named[7773]: managed-keys-zone/reverse-addresses: loaded serial 3
Dec  2 17:39:49 DNS2 named[7773]: managed-keys-zone/reverse-lookup: loaded serial 0
Dec  2 17:39:49 DNS2 named[7773]: managed-keys-zone/internal: loaded serial 248
Dec  2 17:39:49 DNS2 named[7773]: managed-keys-zone/external: loaded serial 3
Dec  2 17:39:49 DNS2 named[7773]: managed-keys-zone/default-zones: loaded serial 248
Dec  2 17:39:49 DNS2 named[7773]: zone 10.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 16.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 24.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 19.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 25.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 20.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 22.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 17.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 18.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 29.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 28.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 21.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 30.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 23.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 26.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 27.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 31.172.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 151.168.192.in-addr.arpa/IN/reverse-lookup: loaded serial 14120103
Dec  2 17:39:49 DNS2 named[7773]: zone 168.192.in-addr.arpa/IN/reverse-addresses: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: zone 150.168.192.in-addr.arpa/IN/reverse-lookup: loaded serial 14120103
Dec  2 17:39:49 DNS2 named[7773]: zone example.com/IN/internal: loaded serial 14120102
Dec  2 17:39:49 DNS2 named[7773]: zone example.com/IN/external: loaded serial 14120103
Dec  2 17:39:49 DNS2 named[7773]: zone 0.in-addr.arpa/IN/default-zones: loaded serial 1
Dec  2 17:39:49 DNS2 named[7773]: zone 255.in-addr.arpa/IN/default-zones: loaded serial 1
Dec  2 17:39:49 DNS2 named[7773]: zone 127.in-addr.arpa/IN/default-zones: loaded serial 1
Dec  2 17:39:49 DNS2 named[7773]: zone localhost/IN/default-zones: loaded serial 2
Dec  2 17:39:49 DNS2 named[7773]: all zones loaded
Dec  2 17:39:49 DNS2 named[7773]: running
Dec  2 17:39:49 DNS2 named[7773]: zone 150.168.192.in-addr.arpa/IN/reverse-lookup: sending notifies (serial 14120103)
Dec  2 17:39:49 DNS2 named[7773]: zone 151.168.192.in-addr.arpa/IN/reverse-lookup: sending notifies (serial 14120103)
Dec  2 17:39:49 DNS2 named[7773]: zone example.com/IN/internal: sending notifies (serial 14120102)
Dec  2 17:39:49 DNS2 named[7773]: client 192.168.151.25#30784: view reverse-addresses: received notify for zone 'example.com': not authoritative

```



If there's any other information that anybody might think is relevant please let me know.

**What I've tried so far:**
- Start fresh without views: Makes the problem go away and it responds fine and in a timely fashion
- Restart the server
- Remove the reverse lookup configuration files
- Set up the configuration files in a different server: I've actually imported the configuration files from a working server, a Fedora 14 is currently working fine with views.
- Remove and re-install bind9
- Remove and re-install apparmor: I had trouble removing it, and so I just disabled it with the same results


The strangest thing here is that it seems to fail right after views are installed and it doesn't fail with error messages.  There are no new entries to the log when I run a query; unless I'm reading the wrong log (which is /var/log/syslog).

Thanks everybody!

Zac

---

### Post by happyraver1958-9 on 2014-12-15
For the people who have been reading this post; I've learned so far that my reverse lookup and/or my rfc1918 zone configuration is the culprit.

As soon as I remove these two from my configuration, my DNS server comes to life!

Right now, after removing the rfc1918 zone file and leaving my reverse lookup file, the log file shows:
```
Dec 15 11:52:30 DNS2 named[30839]: client 192.168.151.25#7544: view reverse-lookup: received notify for zone 'example.com': not authoritative
```
I've read RFC 1918 and it only talks about private and public hosts and networks and how there shall be no leakage of packets from the internal network to the public Internet; but I couldn't connect the dots between that and the entries in the rfc1918 zone file that comes with Ubuntu server by default.
It does however, work fine after I remove the default zone.rfc1918 file from the configuration.
If anybody has a warning for me against doing this, please let me know why because I don't see anything counterproductive in doing so.

Thanks!

Zac

---

### Post by happyraver1958-9 on 2014-12-15
Issue is now solved!
There were several issues with my configuration:
1) My { any; }; keywords for match-clients are out of order.  I should have had the specific match-clients go first, then leave the { any; }; for last.
2) References to forwarding, like forward first; and forwarders should always be used together. If I have a forward first;, I must also have forwarders; if not, remove all references to forwarding to make this a master server.
3) I had too many views.  I only need to have two views for my configuration because I don't have more than one ethernet connection configured in the server and the matching patterns were getting difficult; so only two views, one for internal clients and another one for external clients should work.  Since BIND9 complains about zones not being within views, the best solution to that is to insert those zone references within those two internal and external views so the matching of clients becomes easier for the server to match.
4) I added !192.168/16 clauses to force the server to not match any internal addresses when requests from outside those networks are received; this to avoid further confusion in the configuration.  Make sure you set these !192.168/16 BEFORE the any; clause because if any; is first, BIND9 will ignore any other clauses after that, as can be confirmed if you run a named-checkconf named.conf for your server.
I hope my experience helps other newbies out there!

Zac

---

