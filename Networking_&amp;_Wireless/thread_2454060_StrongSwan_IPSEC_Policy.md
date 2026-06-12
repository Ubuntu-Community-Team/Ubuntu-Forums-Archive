---
title: "StrongSwan IPSEC Policy"
date: 2020-11-22
forum: Networking &amp; Wireless
---

### Post by profil2 on 2020-11-22
Hi,

I need a little help after 3 days of trying, still can't get the desired effect
I have working IPSEC connection A->B and B->C 
How should I set ipsec.conf in SITE B(Ubuntu) to get connection from A->C and C->A using ipsec policy ?

SITE A Mikrotik
local 10.10.0.0/24
Public= 179.x.x.x

SITE B ubuntu serv
local 192.168.0.0/24
Public= 216.x.x.x

SITE C Pfsense
local 192.168.255.0/24
Public=218.x.x.x

conn B->A

        type=tunnel
        auto=add
        keyexchange=ikev2
        authby=secret
        leftid=216.x.x.x
        left=216.x.x.x
        leftsubnet=192.168.0.0/24
        right=179.x.x.x
        rightsubnet=10.10.0.0/24
        ike=aes256-sha1-modp2048!
        esp=aes256-sha1!
        aggressive=no
        keyingtries=%forever
        ikelifetime=28800s
        lifetime=3600s
        dpddelay=30s
        dpdtimeout=120s
        
conn B->C

        type=tunnel
        auto=add
        keyexchange=ikev2
        authby=secret
        leftid=216.x.x.x
        left=216.x.x.x
        leftsubnet=192.168.0.0/24
        right=218.x.x.x
        rightsubnet=192.168.255.0/24
        ike=aes256-sha1-modp2048!
        esp=aes256-sha1!
        aggressive=no
        keyingtries=%forever
        ikelifetime=28800s
        lifetime=3600s
        dpddelay=30s
        dpdtimeout=120s
        dpdaction=restart

---

### Post by profil2 on 2020-11-23
solution - [https://unix.stackexchange.com/questions/620993/strongswan-ipsec-policy](https://unix.stackexchange.com/questions/620993/strongswan-ipsec-policy)

---

