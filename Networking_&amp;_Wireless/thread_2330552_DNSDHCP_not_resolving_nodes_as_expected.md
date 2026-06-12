---
title: "DNS/DHCP not resolving nodes as expected"
date: 2016-07-12
forum: Networking &amp; Wireless
---

### Post by diyhouse on 2016-07-12
I need some help please,.. I have a mixed Msoft windows Linux environment,.. and I have tweaked the config files on my Raspberry Pi with Bind9 and isc-DHCP server for a while now,.. but my tweaks have been in vain....

Although the server routes external DNS requests appropriately,.. I do not seem to be able to route internal requests to LAN nodes, either Fixed IP nodes or DHCP allocated nodes. One obvious ( annoying ) failure is that Msoft windows cannot resolve nodes from a name within explorer,.. I can only use the allocated IP address,

I thought that entering fixed IP address node in the DNS servers /etc/hosts file would mean that would allow "other nodes" to resolve those entries,.. but clearly not,.. as I cannot find them by a simple "ping nodename" or "ping Nodename.domain", but even DHCP allocated nodes cannot be resolved..

What bit of magic am I missing.?

Thankyou for looking..

My Config files are as follows:-
> # Sample of the end of file         /etc/dhcpcd.conf.
.
.
# A hook script is provided to lookup the hostname if not set by the DHCP
# server, but it should not be run by default.
nohook lookup-hostname


interface eth0
static ip_address=192.168.6.240/24
static routers=192.168.6.254
static domain_name_servers=192.168.6.240
----------------------------------------------
;       /etc/bind/zones/6.168.192.in-addr-arpa
; BIND reverse data file for local loopback interface
;
$TTL    604800
$ORIGIN         6.168.192.in-addr.arpa.
@       IN      SOA     ns1.fredtst.co.uk. admin.fredtst.co.uk. (
                     2016240208         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800         ; Negative Cache TTL
)


; name servers - NS records
@      IN      NS      ns1.


localhost       IN A            127.0.0.1


; PTR Records
240     IN      PTR     ns1.fredtst.co.uk.     ; 192.168.6.240
47      IN      PTR     mhtpc.fredtst.co.uk.    ; 192.168.6.47


;; End of Reverse Zone File
-------------------------------------
; /etc/bind/zones/db.fredtst.co.uk
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.fredtst.co.uk. admin.fredtst.co.uk. (
                     2016210503        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;


; name servers - NS records
@          IN      NS      ns1.fredtst.co.uk.


; name servers - A records
ns1          IN      A      192.168.6.240


; PTR Records


; 192.168.6.0/24 - A records
-------------------------------------------
pi@ns1:/etc $ cat resolvconf/update-libc.d/head
# /etc/resolvconf/update-libc.d
search fredtst.co.uk  # your private domain
nameserver 192.168.6.240  # ns1 private IP address
---------------------------------------------
#  /etc/bind/named.conf.local
#
#
# Do any local configuration here
#


# Consider adding the 1918 zones here, if they are not used in your
# organization
# include "/etc/bind/zones.rfc1918";


zone "fredtst.co.uk" {
    type master;
    file "/etc/bind/zones/db.fredtst.co.uk";   # zone file path
    #allow-transfer { 10.128.20.12; };         # ns2 private IP address - secondary
};




zone "6.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/6.168.192.in-addr.arpa";       # 192.168.6.0 Subnet
    #allow-transfer { 10.128.20.12; };           # ns2 private IP address - secondary
};
---------------------------------------------
acl "trusted" {
        192.168.6.240;    # ns1 - can be set to localhost
     localhost;
        localnets;
};


options {
        directory "/var/cache/bind";


        recursion yes;                 # enables resursive queries
        allow-recursion { trusted; };  # allows recursive queries from "trusted" clients
        listen-on { 192.168.6.240; };  # ns1 private IP address - listen on private network only
        allow-transfer { none; };      # disable zone transfers by default




        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)


        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.


        forwarders {
                8.8.8.8;
                8.8.4.4;
        };


        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
-----------------------------------------------
# /etc/hosts
127.0.0.1       localhost
::1             localhost ip6-localhost ip6-loopback
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters


127.0.1.1       ns1 ns1.fredtst.co.uk
192.168.6.47    mhtpc   mhtpc.fredtst.co.uk
192.168.6.15    n5200   n5200.fredtst.co.uk
192.168.6.30    printer printer.fredtst.co.uk
192.168.6.250   waccess waccess.fredtst.co.uk
192.168.6.254   btroute btroute.fredtst.co.uk
192.168.6.33    dabradio        dabradio.fredtst.co.uk




---

