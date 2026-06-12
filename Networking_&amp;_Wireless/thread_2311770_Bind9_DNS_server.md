---
title: "Bind9 DNS server"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by simon126 on 2016-01-29
Hi I'm new to linux and I'm trying to setup Bind9 to run as my server. After following instructions from an online course when I run sudo named-c I get an error

sudo: named-c: command not found

Can someone please help I have attached my files. Thanks in advance

options {
        directory "/var/cache/bind";
        recursion yes;
        allow-recursion {trusted;};
        listen-on{192.168.1.10;};
        allow-transfer{none;};

         forwarders {
                8.8.8.8;
                8.8.4.4;

        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

acl "trusted" {
        192.168.1.0/24;
};

  File: /etc/bind/named.conf.local  

zone "example.com" {
        type master;
        file "/etc/bind/zones/db.example.com";
};

zone  "168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/db.168.192";
};

File: /etc/bind/zones/db.example.com   
$TTL    604800
@       IN      SOA     ns1.example.com. hostmaster.example.com. (
                         2016012901     ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN      NS      ns1.example.com.
ns1     IN      A       192.168.1.1
www     IN      A       192.168.1.1

File: /etc/bind/zones/db.168.192
@       IN      SOA     ns1.example.com. hostmaster.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
192.168.1.1     IN      NS      ns1.example.com.
192.168.1.1     IN      PTR     [www.example.com](www.example.com).

---

### Post by newbie-user on 2016-01-31
named-c? What is that supposed to do? There is no command "named-c", hence the error message.

Perhaps it should be "named -c" (notice the space before the dash), where you want to specify a configuration file? Example: OPTIONS="-u bind -t /chroot/named -c /etc/named.conf"

---

