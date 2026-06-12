---
title: "BIND9 : Forward and reverse zone in the same file ?"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by isakis on 2008-07-17
Hello,

I have been using bind9 on Dapper and Hardy without any problems.

Instead of having set up two separate zone files: one for the forward lookup and one the reverse job, I decided/tried to use a single file. The result was a successful bind9 service !!

However, my concern is whether this approach safe or not. I haven't seen anyone doing this. Is there any security risk having one single file for both zones?

Here is my named.conf.local:

zone "homenet" {
        type master;
        file "/etc/bind/homenet.db";
        notify no;
};

zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/homenet.db";
        notify no;
};

And here is the zone file homenet.db:

$TTL    3D

@ IN SOA ns myemail.example.com. (
	24    ; serial num
	8H    ; refresh, seconds
	2H    ; retry, seconds
	4W    ; expire, seconds
	1D    ; minimum, seconds
)

                NS      ns

printer         A       192.168.0.10
winxp           A       192.168.0.20
ubuntu-server   A       192.168.0.30

xp              CNAME   winxp
ns              CNAME   ubuntu-server

10              PTR     printer.homenet.
20              PTR     winxp.homenet.
30              PTR     ubuntu-server.homenet.





Thank you in advance,
Dennis

---

