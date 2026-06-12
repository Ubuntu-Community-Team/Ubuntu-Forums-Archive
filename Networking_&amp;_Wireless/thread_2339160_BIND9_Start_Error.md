---
title: "BIND9 Start Error"
date: 2016-10-05
forum: Networking &amp; Wireless
---

### Post by buddhaonion on 2016-10-05
My Bind9 server stopped starting up.

Here is the status output:
service bind9 status
&#9679;```
 bind9.service - BIND Domain Name Server
   Loaded: loaded (/lib/systemd/system/bind9.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/bind9.service.d
           &#9492;&#9472;50-insserv.conf-$named.conf
   Active: failed (Result: exit-code) since Tue 2016-10-04 17:02:49 EDT; 17h ago
     Docs: man:named(8)
  Process: 1377 ExecStop=/usr/sbin/rndc stop (code=exited, status=1/FAILURE)
  Process: 1368 ExecStart=/usr/sbin/named -f -u bind (code=exited, status=1/FAILURE)
 Main PID: 1368 (code=exited, status=1/FAILURE)


Oct 04 17:02:49 lab-dnsserver named[1368]: adjusted limit on open files from 4096 to 1048576
Oct 04 17:02:49 lab-dnsserver named[1368]: found 2 CPUs, using 2 worker threads
Oct 04 17:02:49 lab-dnsserver named[1368]: using 2 UDP listeners per interface
Oct 04 17:02:49 lab-dnsserver named[1368]: using up to 4096 sockets
Oct 04 17:02:49 lab-dnsserver named[1368]: loading configuration from '/etc/bind/named.conf'
Oct 04 17:02:49 lab-dnsserver systemd[1]: bind9.service: Main process exited, code=exited, status=1/FAILURE
Oct 04 17:02:49 lab-dnsserver rndc[1377]: rndc: connect failed: 127.0.0.1#953: connection refused
Oct 04 17:02:49 lab-dnsserver systemd[1]: bind9.service: Control process exited, code=exited status=1
Oct 04 17:02:49 lab-dnsserver systemd[1]: bind9.service: Unit entered failed state.
Oct 04 17:02:49 lab-dnsserver systemd[1]: bind9.service: Failed with result 'exit-code'.


Forward Zone File:
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     lab-dnsserver.labzone1.labnet.com. admin.labzone1.labnet.com. (
                              9         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
; name servers - NS records
    IN      NS          lab-dnsserver.labzone1.labnet.com.


; name servers - A records
lab-dnsserver.labzone1.labnet.com.      IN      A       192.168.3.30


; 192.168.3.0/24 - A records
lab-observium.labzone1.labnet.com.      IN      A       192.168.3.31
LAB-2012R2-01.labzone1.labnet.com.      IN      A       192.168.3.21
lab-elk.labzone1.labnet.com.            IN      A       192.168.3.32


Reverse Zone:
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     labzone1.labnet.com. admin.labzone1.labnet.com. (
                              8         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
; name servers - NS records
     IN     NS          lab-dnsserver.labzone1.labnet.com.


; PTR Records
30.3 IN     PTR         lab-dnsserver.labzone1.labnet.com.      ; 192.168.3.30
31.3 IN     PTR         lab-observium.labzone1.labnet.com.      ; 192.168.3.31
21.3 IN     PTR         lAB-2012R2-01.labzone1.labnet.com.      ; 192.168.3.21
32.3 IN     PTR         lab-elk.labzone1.labnet.com.      ; 192.168.3.32

```
I'm not sure where to continue troubleshooting.

Thanks for any help.

---

### Post by buddhaonion on 2016-10-05
Here's the 

```
 named.conf.local
//
// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "labzone1.labnet.com" {
    type master;
    file "/etc/bind/zones/db.labzone1.labnet.com"; # zone file path
    allow-transfer { 192.168.3.31; };         # ns2 private IP address - secondary
    allow-transfer { 192.168.3.32; };
};


zone "168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.168.192";  # 192.168.3.0/24 subnet
    allow-transfer { 192.168.3.31; };  # Observium
    allow-transfer { 192.168.3.32; };  # elk

and 

cat named.conf.local
//
// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "labzone1.labnet.com" {
    type master;
    file "/etc/bind/zones/db.labzone1.labnet.com"; # zone file path
    allow-transfer { 192.168.3.31; };         # ns2 private IP address - secondary
    allow-transfer { 192.168.3.32; };
};


zone "168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.168.192";  # 192.168.3.0/24 subnet
    allow-transfer { 192.168.3.31; };  # Observium
    allow-transfer { 192.168.3.32; };  # elk
};
root@lab-dnsserver:/etc/bind# cat named.conf.options
acl "trusted" {
        192.168.3.30;  # lab-dnsserver - can be set to localhost
        192.168.3.31;  # lab-observium
        192.168.3.32;  # lab-elk
};


options {
        directory "/var/cache/bind";




        recursion yes;                 # enables resursive queries
        allow-recursion { trusted; };  # allows recursive queries from "trusted" clients
        listen-on { 192.168.3.30; };   # ns1 private IP address - listen on private network only
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


        {
        # allow-recursion { 192.168.3.0/24; localhost; };
        };




        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation no;


        auth-nxdomain no;    # conform to RFC1035
        # listen-on-v6 { any; };
};
```

---

### Post by buddhaonion on 2016-10-05
I fixed my own issue. it was a problem in the named.conf.local.

---

### Post by QIII on 2016-10-05
Would you please share what the problem was and what you did to fix it?  That might be helpful to the next person with this issue.

Thanks!

---

### Post by wildmanne39 on 2016-10-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

