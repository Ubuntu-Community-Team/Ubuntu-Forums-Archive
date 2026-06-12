---
title: "Professional Question: DHCP based on mac address"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by tcpip4lyfe on 2008-01-22
Not that this question is professionally written or do I consider myself a linux professional, :) but I do have a question about using DHCP in a business environment. 

I manage about 100 computers and 100 phones.  I just moved over to a class A private address space from class C and moved the DHCP server from our router onto a dapper server.   I have the dhcp3-server package installed and it works great.  I have 2 pools setup:

Pool 1 
10.0.2.1- 10.0.4.254

Pool 2 
10.0.5.1 - 10.0.7.254


Currently the server is randomly assigns address from the two pools and that's fine.  What originally  I wanted to do though was have all the VOIP phones get addresses from Pool 1 and all the PC's get addresses from Pool 2 but I didn't have time. So my question:

How can I get the phones (which all start with the same manufacturer MAC ID 00:0b:82:x:X:x) to dhcp from pool 1 and all the PC's (which all have different MAC's) to come from pool 2?  Is this even possible?  I would like to be able to add a MAC wild card so I can basically say all mac addresses that start with 00.0b.82, get your address from pool 1, if not go to pool 2.  Thanks in advance.

---

### Post by sqrt2 on 2008-01-23
You can define a class "phones", something like this:
```
class "phones" {
   match if substring (hardware, 0, 8) = "00:0b:82";
}
```
and then add the following access policy to your VoIP address pool
```
allow members of "phones";
deny unknown-clients;
```

---

### Post by tcpip4lyfe on 2008-01-24
awesome.  I'll check it out today.

---

### Post by tcpip4lyfe on 2008-01-24
So after a few hours of fighting this Im making a little progress.  First off here's my dhcpd.conf:

```
#DHCP CONFIG

#ddns-update-style ad-hoc;


# option definitions common to all supported networks...
option domain-name "ead-logistics.com";
option domain-name-servers 10.0.0.1, 10.0.0.12, 10.0.0.13;
default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;


# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;



class "phones" {
   match if substring (hardware, 0, 8) = "00:0b:82";
}

# 10.0.0.0
subnet 10.0.0.0 netmask 255.255.0.0 {
	pool {
		range 10.0.5.1 10.0.7.254;
		allow members of "phones";
		deny unknown-clients;
		}
	}

```

I've simplified it down for testing purposes by removing the second pool. Im guessing the problem is with my ACL because it pulls an address without thems. I've tried the entire changing 

class "phones" {
   match if substring (hardware, 0, 8) = "00:0b:82"; to 



class "phones" {
   match if substring (hardware, 0, 17) = "entire mac address";

I've tried putting it in different parts of the conf file and I've tried different versions of the "match if substring" statement.  Im stumped.  Anyone have any ideas?  This is what I get when I start the DHCP server and fire up the phone:


admin@testbed2:~$ sudo dhcpd3 -d -f 2>&1
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 0 leases to leases file.
Listening on LPF/eth0/00:16:76:5c:fc:bc/10.0/16
Sending on   LPF/eth0/00:16:76:5c:fc:bc/10.0/16
Sending on   Socket/fallback/fallback-net
DHCPDISCOVER from 00:0b:82:0d:f2:c5 via eth0: network 10.0/16: no free leases
DHCPDISCOVER from 00:0b:82:0d:f2:c5 via eth0: network 10.0/16: no free leases
DHCPDISCOVER from 00:0b:82:0d:f2:c5 via eth0: network 10.0/16: no free leases

---

### Post by tcpip4lyfe on 2008-01-24
Solution: 
Had the wrong syntax. Thanks for pointing me in the right direction though. 

```
#DHCP CONFIG

#ddns-update-style ad-hoc;


# option definitions common to all supported networks...
option domain-name "ead-logistics.com";
option domain-name-servers 10.0.0.1, 10.0.0.12, 10.0.0.13;
default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;


# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

[B]class "phones" {
	match if substring (hardware,1,3) = 00:0b:82;[/B]
}

# 10.0.0.0
subnet 10.0.0.0 netmask 255.255.0.0 {
	pool {
		range 10.0.5.1 10.0.7.254;
		allow members of "phones";
                deny unknown-clients
		}
	pool {
		allow unknown-clients;
		range 10.0.2.1 10.0.4.254;
		deny members of "phones";
		}
	}



```

---

