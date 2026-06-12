---
title: "network Bind9 and DHCP"
date: 2016-02-20
forum: Networking &amp; Wireless
---

### Post by diyhouse on 2016-02-20
I have scanned forms a posts,.. and I am still missing the last pieces of the jigsaw,...

I have configured myself a Bind9 DNS server,.. as well as a ISC-DHCP_server,.... on the same machine,.. ( Rasp-Pi )

Things sort of work,.. my network connected m/cs will look at new websites without any issues,.. and new IP addresses are allocated as required,.... But local DNS lookups do not work correctly,.. other than for addresses which I have manually edited into the name-servers hosts file....

Local lookups from client to client don't work as I'm not sure dhcp addresses/names are being entered into a database that can be looked-up by dns,.. or an I missing something here,... "Should the DHCP server" enter addresses that are then resolvable by DNS... or is this a miss-conception... or do I have to manually edit somewhere,.. ( seems to be flawed argument though )

Also I'm a little confused on my reverse Zone file,...  my entries look as follows:- ( with some preamle stuff and the file is duly called db.168.192
.
; PTR Records
3.240      IN      PTR     ns1.hamblin.me.uk.     ; 192.168.3.240

Now my question is do need 3.240,.. as the ip address,.. or is it simply "240",..  guides I have found are unclear,.. and seem to do it either way,... so slightly confused.... which is the correct way of entering these reverse Ip addresses...

Can someone help fill in my gaps,.. 
Many thanks

---

### Post by newbie-user on 2016-02-22
A couple of things to check:
1. Make sure your DHCP server is set up to send the address of your local DNS server as the primary dns server:
```
options domain-name-servers [address of your dns server];
```
2. Check your forward-lookup file on your DNS server. You may still have to add the hosts to resolve.
3. Check that your client computers are using your local DNS server.

---

### Post by diyhouse on 2016-02-23
Yes,.. Thanks for that,.. some useful thoughts,...  some of my linux m/cs have fixed I/P addresses... and they are not privileged to know about the DNS change,... Yet.... But PCs which get their IP via dhcp,... Do know about the change of DNS,... but equally cannot use it as yet for some reason. ( internal zone searches fail,.. external searches work fine ) have tried some more edits,... and got a little further with understanding Bind errors... But have now sort of walled and going round in circles again...
Have included the Bind file as a single list,.. if anyone can spread any light on my miss-understanding...

If anyone can point me as to my errors,.. very much appreciated...

************************

> # Sample of the end of file 		/etc/dhcpcd.conf.
.
.
# A hook script is provided to lookup the hostname if not set by the DHCP
# server, but it should not be run by default.
nohook lookup-hostname


interface eth0
static ip_address=192.168.5.240/24
static routers=192.168.5.254
static domain_name_servers=192.168.5.240


******************************************************************
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.doName.com. admin.doName.com. (
                     2016220206         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;


; name servers - NS records
      IN      NS      ns1.doName.com.


; server host definitions
240      IN  PTR    ns1.doName.com.     
      
      
; PTR Records
240     IN      PTR     ns1.doName.com.     ; 192.168.5.240
47	IN	PTR	mhtpc.doName.com	; 192.168.5.47
******************************************************************
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.doName.com. admin.doName.com. (
                     2015121602         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;


; name servers - NS records
doName.com.    IN      NS      ns1.doName.com.




; name servers - A records
ns1          IN      A      192.168.5.240




; 192.168.5.0/24 - A records
*****************************************************************
# /etc/resolvconf/update-libc.d/head
search doName.com  # your private domain
nameserver 192.168.5.240  # ns1 private IP address
****************************************************************
#  /etc/bind/named.conf.local
#
#
# Do any local configuration here
#


# Consider adding the 1918 zones here, if they are not used in your
# organization
# include "/etc/bind/zones.rfc1918";


zone "doName.com" {
    type master;
    file "/etc/bind/zones/db.doName.com";   # zone file path
    #allow-transfer { 10.128.20.12; };         # ns2 private IP address - secondary
};




zone "3.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.5.168.192"; 	 # 192.168.5.0 Subnet
    #allow-transfer { 10.128.20.12; };		 # ns2 private IP address - secondary
};
************************************************************************
acl "trusted" {
        192.168.5.240;    # ns1 - can be set to localhost
 	localhost;
        localnets;
};




options {
        directory "/var/cache/bind";


        recursion yes;                 # enables resursive queries
        allow-recursion { trusted; };  # allows recursive queries from "trusted" clients
        listen-on { 192.168.5.240; };  # ns1 private IP address - listen on private network only
        allow-transfer { none; };      # disable zone transfers by default


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




---

### Post by SeijiSensei on 2016-02-23
The reverse zones should include all three leading octets. For instance, the SOA for my reverse zone is for 100.168.192.in-addr.arpa. The hosts then have PTR records for hosts 1, 2, etc.

---

### Post by diyhouse on 2016-03-03
Thank you so much for your pointer,.... took me a while to get it working,.. but then noticed I had missed the trailing  "." from ....arpa.   
...but have been running things now for about a week and all seem to be working OK

Many thanks again 
and rgds

---

