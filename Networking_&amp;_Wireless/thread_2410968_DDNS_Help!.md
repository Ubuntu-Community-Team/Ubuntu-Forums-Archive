---
title: "DDNS Help!"
date: 2019-01-23
forum: Networking &amp; Wireless
---

### Post by tarxsix on 2019-01-23
Hello, I've been trying to set up DDNS for days now. I got it to the point where I could resolve hosts but I had the error "Unable to add forward map" but then started getting "ns.domain.ca: temporary name server failure" and DNS would not work at all.
Below are logs and configs:

syslog:
----
Jan 22 09:50:12 delle6430 named[2920]: zone 127.in-addr.arpa/IN: loaded serial 1
Jan 22 09:50:12 delle6430 named[2920]: zone domain.ca/IN: NS 'ns.domain.ca' has no address records (A or AAAA)
Jan 22 09:50:12 delle6430 named[2920]: zone domain.ca/IN: not loaded due to errors.
Jan 22 09:50:12 delle6430 named[2920]: zone 0.168.192.in-addr.arpa/IN: loaded serial 6
Jan 22 09:50:12 delle6430 named[2920]: zone 255.in-addr.arpa/IN: loaded serial 1
Jan 22 09:50:12 delle6430 named[2920]: zone localhost/IN: loaded serial 2
Jan 22 09:50:12 delle6430 named[2920]: all zones loaded
Jan 22 09:50:12 delle6430 named[2920]: running
Jan 22 09:50:13 delle6430 named[2920]: managed-keys-zone: Key 20326 for zone . acceptance timer complete: key now trusted
Jan 22 09:50:13 delle6430 named[2920]: resolver priming query complete
Jan 22 09:50:32 delle6430 named[2920]: message repeated 2 times: [ resolver priming query complete]
Jan 22 09:50:36 delle6430 dhcpd[2860]: DHCPREQUEST for 192.168.0.121 from mac (host1) via eno1
Jan 22 09:50:36 delle6430 dhcpd[2860]: ns.domain.ca: temporary name server failure
Jan 22 09:50:36 delle6430 dhcpd[2860]: DHCPACK on 192.168.0.121 to mac (host1) via eno1
Jan 22 09:50:36 delle6430 dhcpd[2860]: DDNS: cleaning up lease pointer for a cancel cb=0x55fd8ab603b0
Jan 22 09:50:36 delle6430 dhcpd[2860]: Unable to add forward map from host1.domain.ca to 192.168.0.121: operation canceled
Jan 22 09:50:43 delle6430 kernel: [ 5243.753758] [UFW BLOCK] IN=eno1 OUT= MAC=mac SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2


Jan 22 10:56:48 delle6430 dhcpd[2860]: DHCPREQUEST for 192.168.0.111 from mac (android-1) via eno1
Jan 22 10:56:49 delle6430 dhcpd[2860]: ns.domain.ca: temporary name server failure
Jan 22 10:56:49 delle6430 dhcpd[2860]: DHCPACK on 192.168.0.111 to mac (android-1) via eno1
Jan 22 10:56:49 delle6430 dhcpd[2860]: DDNS: cleaning up lease pointer for a cancel cb=0x55fd8ab65150
Jan 22 10:56:49 delle6430 dhcpd[2860]: Unable to add forward map from android-1.domain.ca to 192.168.0.111: operation canceled
----


zone links:
----
:~$ sudo ls -l /var/cache/bind/
total 8
lrwxrwxrwx 1 root root  28 Jan 21 13:49 db.192.168.0 -> /etc/bind/zones/db.192.168.0
lrwxrwxrwx 1 root root  31 Jan 22 06:51 db.domain.ca -> /etc/bind/zones/db.domain.ca
-rw-r--r-- 1 bind bind 821 Jan 22 08:28 managed-keys.bind
-rw-r--r-- 1 bind bind 512 Jan 22 08:28 managed-keys.bind.jnl
----


/etc/bind/named.conf.local:
----
include "/etc/bind/ddns.key";


zone "domain.ca"  {
    type master;
    notify no;
    file "/var/cache/bind/db.domain.ca"; # zone file path
    allow-query { 192.168.0.0/24; 127.0.0.1; };
    allow-update { key DDNS_UPDATE; };
};


zone "0.168.192.in-addr.arpa" {
    type master;
    notify no;
    file "/var/cache/bind/db.192.168.0"; # 192.168.0.0 subnet
    allow-query { 192.168.0.0/24; 127.0.0.1; };
    allow-update { key DDNS_UPDATE; };
};
-----


/etc/bind/zones/db.domain.ca
---
$TTL    604800
@       IN      SOA     domain.ca. root.domain.ca. (
                              6         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;




@       IN      NS      ns.domain.ca.
ns      IN      A       192.168.0.106
----


/etc/bind/zones/db.192.168.0
----
$TTL    604800
@       IN      SOA     domain.ca. root.domain.ca. (
                              6         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;


@       IN      NS      ns.domain.ca.
106     IN      PTR     ns.domain.ca.
----


/etc/dhcp/dhcpd.conf
-----
authoritative;
option domain-name "domain.ca";
option domain-name-servers ns.domain.ca;


ddns-updates on;
ddns-update-style interim;
ignore client-updates;
update-static-leases on;


default-lease-time 600;
max-lease-time 7200;
log-facility local7;


include "/etc/dhcp/ddns.key";


zone domain.ca. {
  primary 127.0.0.1;
  key DDNS_UPDATE;
}


zone 0.168.192.in-addr.arpa. {
  primary 127.0.0.1;
  key DDNS_UPDATE;
}


subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.110 192.168.0.210;
  option routers 192.168.0.1;
}
-----


50-cloud-init.yaml:
----
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
     addresses: [192.168.0.106/24]
     dhcp4: no
     gateway4: 192.168.0.1
     nameservers:
       addresses: [192.168.0.106]
-----


00-private-nameservers.yaml:
-----
network:
  version: 2
  ethernets:
    eno1:                                                       # private network interface
     nameservers:
       addresses:
       - 192.168.0.106                          # private IP for DNS
       search: [ domain.ca ]       # DNS zone
-----

---

### Post by tarxsix on 2019-01-23
forgot:

/etc/default/bind9
----
RESOLVCONF=no


# startup options for the server
OPTIONS="-u bind"
----


/etc/bind/named.conf.options
---
acl "trusted" {
        192.168.0.106;  # DNS server
        192.168.0.0/24;
        localhost;
        localnets;
};


options {
        directory "/var/cache/bind";




        recursion yes;                  # enables resursive queries
        allow-recursion { trusted; };   # allows recursive queries from "trusted" clients
        listen-on { 192.168.0.106; };   # ns private IP address - listen on private network only
        allow-transfer { none; };       # disable zone transfers by default       


 forwarders {
                8.8.8.8;
                8.8.4.4;
        };


        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)


        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.


        // forwarders {
        //      0.0.0.0;
        // };


        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

---

### Post by SeijiSensei on 2019-01-23
You seemed to have missed this:

```

Jan 22 09:50:12 delle6430 named[2920]: zone domain.ca/IN: NS 'ns.domain.ca' has no address records (A or AAAA)
Jan 22 09:50:12 delle6430 named[2920]: zone domain.ca/IN: not loaded due to errors.

```

---

### Post by tarxsix on 2019-01-23
that started showing up when "[COLOR=#000000]ns.domain.ca: temporary name server failure" started. nothing was changed, so not sure or at lease not seeing where the problem is[/COLOR]

---

### Post by SeijiSensei on 2019-01-23
The error is pretty clear.  You have no hosts defined in the zone file for ns.domain.ca.  

It could be that stray semicolon in the zone file.  DNS is **very** strict about formatting.  Here's a sample of one of mine:

```
$TTL 86400      ; 1 day

@               IN     SOA      example.com. support.example.com. (
                                2018100801 ; serial
                                43200      ; refresh (12 hours)
                                3600       ; retry (1 hour)
                                86400      ; expire (1 day)
                                43200      ; minimum (12 hours)
                                )

                IN      NS      example.example.com.
                IN      NS      ns.example.com.
                IN      NS      ns2.example.com.

                IN      MX      0 example.example.com.
                IN      MX      5 smtp.example.com.

localhost       IN      A       127.0.0.1

ns2             IN      A       97.107.141.13
smtp            IN      A       97.107.141.13

ns              IN      A       50.116.11.117

[etc.]

```

---

### Post by tarxsix on 2019-01-23
There's something I'm not understanding, still getting the same error.
This is what I did:

```

$TTL    604800@               IN      SOA     domain.ca. root.domain.ca. (
                              7         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL




                IN      NS      delle6430.domain.ca.


localhost       IN      A       127.0.0.1


ns              IN      A       192.168.0.106

```

---

### Post by tarxsix on 2019-01-23
ok, I got rid of the "zone domain.ca/IN: NS 'ns.domain.ca' has no address records (A or AAAA)" error by changing the zone file to:
---
```

$TTL    604800@               IN      SOA     domain.ca. root.domain.ca. (
                              9         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL




                IN      NS      delle6430.domain.ca.


localhost       IN      A       127.0.0.1


delle6430.domain.ca.         IN      A       192.168.0.106

```

but now I'm back to error:
 "Jan 23 16:28:35 delle6430 dhcpd[6294]: DHCPREQUEST for 192.168.0.126 from mac (android-1) via eno1Jan 23 16:28:35 delle6430 dhcpd[6294]: DHCPACK on 192.168.0.126 to mac (android-1) via eno1
Jan 23 16:28:35 delle6430 dhcpd[6294]: DDNS: cleaning up lease pointer for a cancel cb=0x558c63be4180
Jan 23 16:28:35 delle6430 dhcpd[6294]: **Unable to add forward map from** android-1.domain.ca to 192.168.0.126: operation canceled:

Can anyone help with this?

my reverse zone:
```

$TTL    604800
@       IN      SOA     domain.ca. root.domain.ca. (
                              8         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL


@       IN      NS      delle6430.domain.ca.
106     IN      PTR     delle6430.domain.ca.

```

---

### Post by SeijiSensei on 2019-01-23
I've not used dynamic updates via dhcpd, but I'd check on the correct permissions to make sure dhcpd can rewrite the necessary files.  

Just a guess.

---

### Post by tarxsix on 2019-01-24
I think all my permissions are ok:

```

/var/cache/drwxrwxr-x  2 root      bind 4096 Jan 23 16:28 bind
/etc/bind/
drwxr-sr-x 2 root bind 4096 Jan 23 18:51 zones
/etc/bind/zones/
-rw-r--r-- 1 root bind 293 Jan 23 16:26 db.192.168.0
-rw-r--r-- 1 root bind 330 Jan 23 16:27 db.domain.ca

```

there is one thing:

```

/etc/resolv.conf---
domain domain.ca
search domain.ca
nameserver 127.0.0.53

```

Why is that ns 53? If I change it to .1, dns stops working again. The ns with 53 was there before I set anything up. Should I add a ns .1 here or add the .53 ns in the other config files?
Edit: adding the ns .1 to resolv.conf does not seem to do anything

---

### Post by SeijiSensei on 2019-01-24
It's the way systemd-resolve works.

[http://man7.org/linux/man-pages/man1/systemd-resolve.1.html](http://man7.org/linux/man-pages/man1/systemd-resolve.1.html)

DNS resolution is, to my mind, a contorted mess. This is the 2nd method employed in the past few years. Each change makes it more difficult to figure out how to set up a static resolv.conf.

---

