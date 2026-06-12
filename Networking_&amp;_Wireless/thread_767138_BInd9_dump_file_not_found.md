---
title: "BInd9 dump file not found"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Rever75 on 2008-04-25
Hi I am trying to configure my linux box to act as a secondary DNS Server to our AD environment. I have followed a bunch of 
instructions and read a few manuals. I have the system installed chroot. However I am not getting anything. Here is my 
config files and daemon.log dump....

 **name.conf**
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

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

include "/etc/bind/named.conf.local";
```

**name.conf.options**
```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	// query-source address * port 53;

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	 forwarders {
	 	208.67.222.222;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```

**name.conf.local**
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
#This is my Zone definition for for my internal AD DNS
zone "my.local" {
	type slave;
	file "/var/lib/named/bind/my.local";
	masters {192.168.150.35; 192.168.150.31; };
	};

```
[B]
daemon.log [/B]
```
Apr 25 14:44:28 crandns named[5697]: loading configuration from '/etc/bind/named.conf'
Apr 25 14:44:28 crandns named[5697]: zone my.local/IN: Transfer started.
Apr 25 14:44:28 crandns named[5697]: transfer of 'my.local/IN' from 192.168.150.35#53: connected using 192.168.148.200#45492
Apr 25 14:44:28 crandns named[5697]: dumping master file: /var/lib/named/bind/tmp-4SWo6ZkPNp: open: file not found
Apr 25 14:44:28 crandns named[5697]: transfer of 'my.local/IN' from 192.168.150.35#53: failed while receiving responses: 
file not found
Apr 25 14:44:28 crandns named[5697]: transfer of 'my.local/IN' from 192.168.150.35#53: end of transfer
Apr 25 14:44:28 crandns named[5697]: zone my.local/IN: Transfer started.
Apr 25 14:44:28 crandns named[5697]: transfer of 'my.local/IN' from 192.168.150.31#53: connected using 192.168.148.200#40466
Apr 25 14:44:28 crandns named[5697]: dumping master file: /var/lib/named/bind/tmp-tOE3kyU1S7: open: file not found
Apr 25 14:44:28 crandns named[5697]: transfer of 'my.local/IN' from 192.168.150.31#53: failed while receiving responses: 
file not found
Apr 25 14:44:28 crandns named[5697]: transfer of 'my.local/IN' from 192.168.150.31#53: end of transfer

```

I have allowed zone transfers to this Server and also checked off Bind Secondaries in the Advanced Tab of my server 2003 AD 
DNS. The log shows the Transfers as successful  but my Linux Server gives me the [B]dumping master file: 
/var/lib/named/bind/tmp-tOE3kyU1S7: open: file not found[/B]. Any help would be greatly appreciated.
There is no firewall between these systems as I am on a /22 network so they are on the same subnet. This is on a Hardy Server install with bind from the repos.

---

### Post by Rever75 on 2008-04-29
Well I solved my issue. Looks like I in the names.conf.options I had coded that the file would be in a specific directory. Then in my names.conf.local file I placed the full path to the file when all I needed to do was place the file name for the database.

---

