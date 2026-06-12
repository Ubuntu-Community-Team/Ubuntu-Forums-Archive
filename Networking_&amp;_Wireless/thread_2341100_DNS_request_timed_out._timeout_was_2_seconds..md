---
title: "DNS request timed out. timeout was 2 seconds."
date: 2016-10-24
forum: Networking &amp; Wireless
---

### Post by rzombie33 on 2016-10-24
Hi All.

I'm trying to setup a private LAN that hosts a private website for those connected to the network.


**Environment:**
- Private LAN
- 1 Wireless Router
- 1 Ubuntu Server 16.04.1 LTS
- X Windows/Mac's connected to the router via wifi


**Configurations:**
- Ubuntu Server has a static IP (192.168.1.3) given by the router. (NIC on server is configured as DHCP)
- Wireless Router has its DNS servers configured to the Ubuntu Server (192.168.1.3)
- Ubuntu Server has Bind9 installed
- Ubuntu Server is hosting a basic website "www.example.com"
- I've configured a new forward and reverse DNS zone following the instructions at [https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html) for the website "www.example.com"
 
**Issue:**
1. On a Windows 7 Laptop, I use Chrome to access the website "www.example.com" and find that it takes 20-30 seconds to resolve the first page. Once the first page loads (e.g. homepage), all other subsequent pages on the website load at a faster rate (this includes the first page).
2. On a Windows 7 laptop, connected to the LAN, using nslookup always results in the following


```
C:\Users\User> nslookup example.com
Server: UnKnown
Address: 192.168.1.3


DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
Name:     example.com
Address: 192.168.1.3

```
3. When I use Dig on the server... it works.... here's the results:
```

administrator@server01:~$ dig example.com


; <<>> DiG 9.10.3-P4-Ubuntu <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52946
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;example.com.                        IN      A


;; ANSWER SECTION:
example.com.         604800  IN      A       192.168.1.3


;; AUTHORITY SECTION:
example.com.         604800  IN      NS      example.com.


;; Query time: 0 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Oct 25 11:10:12 AEDT 2016
;; MSG SIZE  rcvd: 73


administrator@server01:~$



```



Can anyone help me in resolving issue 1 and 2? Or point me in a direction of where to start looking.
Thanks!


Bind files:


/etc/bind/db.192
```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    example.com. root.example.com. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.
10    IN    PTR    ns.example.com.

```

/etc/bind/db.example
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    example.com. root.example.com. (
                 12        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    example.com.
@    IN    A    192.168.1.3
www    IN    A    192.168.1.3

```



/etc/bind/named.conf.default-zones
```
// prime the server with knowledge of the root servers
zone "." {
    type hint;
    file "/etc/bind/db.root";
};


// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912


zone "example.com" {
    type master;
    file "/etc/bind/db.example";
};


zone "192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.192";
};


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



```

/etc/bind/named.conf.options
```

acl goodclients {
    192.168.1.0/24;
    localhost;
    localnets;
};


options {
    directory "/var/cache/bind";


    recursion yes;
    allow-query {goodclients; };


    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113


    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.


    //forwarders {
    //     8.8.8.8; // Google DNS Server
    //    8.8.4.4; // Google DNS Server
    //};


    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //========================================================================
    dnssec-enable yes;
    dnssec-validation yes;


    auth-nxdomain no;    # conform to RFC1035
    listen-on { any; };
    listen-on-v6 { any; };
};

```

---

