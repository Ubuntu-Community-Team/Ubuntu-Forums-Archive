---
title: "2 IP addresses from DHCP"
date: 2018-05-12
forum: Networking &amp; Wireless
---

### Post by DarkAmbient on 2018-05-12
Hello!

I'm trying to setup a DDNS-server in my home. I've managed to get DHCP and DNS to work together, connected devices gets mapped to device-name.domain-name. 

My home network **1.1.1.0/24**, and the home domain is called **home**. So my laptop "ti7", upon connected, gets added to the dns as ti7.home by the dhcp-service.

This works well and all, but there's only one thing that annoys me, I get 2 IP addresses from the DHCP "one some connected devices". Sometimes I get 1 IP, and after a while the second one gets assigned.

If this problem has nothing to do with DNS being involved I apologize for providing all the information about it, DHCP configuration is further down.

**gw** is my router, with DCHP turned off, it has IP **1.1.1.1**.
**ns1** is the DDNS, it has static IP **1.1.1.2**.
**ns2** is a slave DNS it has static IP **1.1.1.3**. (although I'm sure this one can't be relevant for this issue)

So all the configuration really is on ns1, I use bind for DNS and isc-dhcp-server for DHCP.

Bind configuration: 

```
root@ns1:/etc/bind# cat named.conf
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
```

```
root@ns1:/etc/bind# cat named.conf.options 
acl "trusted" {
	1.1.1.0/24;
	127.0.0.1/32;
	::1;
};

acl "internet" {
	any;
};

options {

	directory "/var/cache/bind";

	listen-on port 53 {
		1.1.1.2;
		127.0.0.1;
	};

	listen-on-v6 port 53 {
		none;
	};

	forwarders {
		8.8.8.8;
		8.8.4.4;
	};

	dnssec-enable	 	yes;
	dnssec-validation	yes;
	
	recursion			yes;

	allow-recursion {
		trusted;
	};

	allow-transfer {
		1.1.1.3;
	};

	allow-query { 
		trusted;
	};
};
```


```
root@ns1:/etc/bind# cat named.conf.local 
include "/etc/bind/ddns.key"; # DDNS key is specified here

zone "home" {
	
	type master;
	notify yes;

	allow-transfer {
		1.1.1.3;
	};

	allow-update {
		key DDNS;
	};
	
	file "/etc/bind/zones/db.home";
};

zone "1.1.1.in-addr.arpa" {
	
	type master;
	notify yes;

	allow-transfer {
		1.1.1.3;
	};

	allow-update {
		key DDNS;
	};
	
	file "/etc/bind/zones/db.1.1.1";
};
```


And for the zones:

Forward:
```
root@ns1:/etc/bind/zones# cat db.home
$ORIGIN .
$TTL 604800	; 1 week
home			IN SOA	ns1.home. root.home. (
				134        ; serial
				604800     ; refresh (1 week)
				86400      ; retry (1 day)
				2419200    ; expire (4 weeks)
				604800     ; minimum (1 week)
				)
			NS	ns1.home.
			NS	ns2.home.
$ORIGIN home.
$TTL 3600	; 1 hour
iPhone			A	1.1.1.102
			TXT	"31c8a1b554bc46ea119785e7c55e829871"
$TTL 604800	; 1 week
ns1			A	1.1.1.2
ns2			A	1.1.1.3
p			CNAME	printer
$TTL 3600	; 1 hour
ti7			A	1.1.1.104
			TXT	"000b3b4befb738597dfec482adacc014e4"
$TTL 604800	; 1 week
.. some cnames ...

```

The ti7 and TXT line was added by the DHCP-service.
Reverse:
```
root@ns1:/etc/bind/zones# cat db.1.1.1
$ORIGIN .
$TTL 604800	; 1 week
1.1.1.in-addr.arpa	IN SOA	ns1.home. root.home. (
				134        ; serial
				604800     ; refresh (1 week)
				86400      ; retry (1 day)
				2419200    ; expire (4 weeks)
				604800     ; minimum (1 week)
				)
			NS	ns1.home.
			NS	ns2.home.
$ORIGIN 1.1.1.in-addr.arpa.
$TTL 3600	; 1 hour
102			PTR	iPhone.home.
104			PTR	ti7.home.
$TTL 604800	; 1 week
2			PTR	ns1.home.
3			PTR	ns2.home.
```

The 104 PTR for ti7.home was added by the DHCP-service.

The zones checks out OK:
```
root@ns1:/etc/bind/zones# named-checkzone home db.home
zone home/IN: loaded serial 133
OK
```
```
root@ns1:/etc/bind/zones# named-checkzone 1.1.1.in-addr.arpa db.1.1.1
zone 1.1.1.in-addr.arpa/IN: loaded serial 133
OK

```


For the DHCP part:

```
root@ns1:/etc/dhcp# cat dhcpd.conf 
include "/etc/bind/ddns.key";

ddns-updates on;
ddns-update-style interim;
update-static-leases on;
allow unknown-clients;
use-host-decl-names on;
one-lease-per-client true;

default-lease-time 1814400; # 21 days
max-lease-time 1814400; # 21 days

log-facility local7;

zone home. {
	primary 127.0.0.1;
	key DDNS;
}

zone 1.1.1.in-addr.arpa. {
	primary 127.0.0.1;
	key DDNS;
}

subnet 1.1.1.0 netmask 255.255.255.0 {
 	range 1.1.1.100 1.1.1.200;	
	option subnet-mask 255.255.255.0;
	option routers 1.1.1.1;
	option domain-name-servers 1.1.1.2,1.1.1.3;
	option domain-name "home";
	ddns-domainname "home.";
	ddns-rev-domainname "in-addr.arpa.";
}
```

Everything "seems to be working", but I find it strange that when I check leases I get multiple ones for the same device:

```
root@ns1:~# cat /var/lib/dhcp/dhcpd.leases
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-4.3.1

server-duid "\000\001\000\001\"\211\2421\270'\353\273\246\353";

lease 1.1.1.104 {
  starts 6 2018/05/12 13:01:49;
  ends 6 2018/06/02 13:01:49;
  cltt 6 2018/05/12 13:01:49;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet c8:f7:33:90:1c:03;
  client-hostname "ti7";
}
lease 1.1.1.104 {
  starts 6 2018/05/12 13:01:49;
  ends 6 2018/06/02 13:01:49;
  cltt 6 2018/05/12 13:01:49;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet c8:f7:33:90:1c:03;
  set ddns-txt = "000b3b4befb738597dfec482adacc014e4";
  set ddns-fwd-name = "ti7.home.";
  client-hostname "ti7";
}
lease 1.1.1.104 {
  starts 6 2018/05/12 13:01:49;
  ends 6 2018/06/02 13:01:49;
  cltt 6 2018/05/12 13:01:49;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet c8:f7:33:90:1c:03;
  set ddns-rev-name = "104.1.1.1.in-addr.arpa.";
  set ddns-txt = "000b3b4befb738597dfec482adacc014e4";
  set ddns-fwd-name = "ti7.home.";
  client-hostname "ti7";
}
lease 1.1.1.103 {
  starts 6 2018/05/12 13:01:49;
  ends 6 2018/06/02 13:01:49;
  cltt 6 2018/05/12 13:01:49;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet c8:f7:33:90:1c:03;
  uid "\3773\220\034\003\000\001\000\001\037\0312;\310\3673\220\034\003";
  client-hostname "ti7";
}
lease 1.1.1.103 {
  starts 6 2018/05/12 13:01:49;
  ends 6 2018/05/12 13:15:09;
  tstp 6 2018/05/12 13:15:09;
  cltt 6 2018/05/12 13:01:49;
  binding state free;
  hardware ethernet c8:f7:33:90:1c:03;
  uid "\3773\220\034\003\000\001\000\001\037\0312;\310\3673\220\034\003";
}
lease 1.1.1.103 {
  starts 6 2018/05/12 13:15:10;
  ends 6 2018/06/02 13:15:10;
  cltt 6 2018/05/12 13:15:10;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet c8:f7:33:90:1c:03;
  uid "\3773\220\034\003\000\001\000\001\037\0312;\310\3673\220\034\003";
  client-hostname "ti7";
}
lease 1.1.1.102 {
  starts 6 2018/05/12 13:42:48;
  ends 6 2018/06/02 13:42:48;
  cltt 6 2018/05/12 13:42:48;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 98:9e:63:66:67:3b;
  uid "\001\230\236cfg;";
  client-hostname "iPhone";
}
lease 1.1.1.102 {
  starts 6 2018/05/12 13:42:48;
  ends 6 2018/06/02 13:42:48;
  cltt 6 2018/05/12 13:42:48;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 98:9e:63:66:67:3b;
  uid "\001\230\236cfg;";
  set ddns-txt = "31c8a1b554bc46ea119785e7c55e829871";
  set ddns-fwd-name = "iPhone.home.";
  client-hostname "iPhone";
}
lease 1.1.1.102 {
  starts 6 2018/05/12 13:42:48;
  ends 6 2018/06/02 13:42:48;
  cltt 6 2018/05/12 13:42:48;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 98:9e:63:66:67:3b;
  uid "\001\230\236cfg;";
  set ddns-rev-name = "102.1.1.1.in-addr.arpa.";
  set ddns-txt = "31c8a1b554bc46ea119785e7c55e829871";
  set ddns-fwd-name = "iPhone.home.";
  client-hostname "iPhone";
}

```

On the laptop "ti7":

```
r@ti7:~$ ip a | grep global
    inet 1.1.1.104/24 brd 1.1.1.255 scope global dynamic wlp2s0
    inet 1.1.1.103/24 brd 1.1.1.255 scope global secondary wlp2s0
```

Iv'e tried to halt bind and stop dhcp.. removing cache and added entries:

```

root@ns1:~# systemctl stop isc-dhcp-server
root@ns1:~# rndc freeze
# manually removing dhcp entries added by dhcp in local domain zones
root@ns1:~# >/var/lib/dhcp/dhcpd.leases
root@ns1:~# rm /var/lib/dhcp/dhcpd.leases~ 
root@ns1:~# rndc thaw
root@ns1:~# systemctl start isc-dhcp-server

```

Then reconnect, still get 2 IP addresses on ti7.

I get some these errors from syslog:

```
May 12 15:01:39 ns1 isc-dhcp-server[5634]: Starting ISC DHCP server: dhcpd.
May 12 15:01:39 ns1 systemd[1]: Started LSB: DHCP server.
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: signer "ddns" approved
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': adding an RR at 'ti7.home' A
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': adding an RR at 'ti7.home' TXT
May 12 15:01:49 ns1 dhcpd: DHCPREQUEST for 1.1.1.104 from c8:f7:33:90:1c:03 via eth0
May 12 15:01:49 ns1 dhcpd: DHCPACK on 1.1.1.104 to c8:f7:33:90:1c:03 (ti7) via eth0
May 12 15:01:49 ns1 named[5570]: zone home/IN: sending notifies (serial 133)
May 12 15:01:49 ns1 dhcpd: Added new forward map from ti7.home. to 1.1.1.104
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: signer "ddns" approved
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone '1.1.1.in-addr.arpa/IN': deleting rrset at '104.1.1.1.in-addr.arpa' PTR
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone '1.1.1.in-addr.arpa/IN': adding an RR at '104.1.1.1.in-addr.arpa' PTR
May 12 15:01:49 ns1 named[5570]: client 1.1.1.3#52500 (home): transfer of 'home/IN': IXFR started
May 12 15:01:49 ns1 named[5570]: client 1.1.1.3#52500 (home): transfer of 'home/IN': IXFR ended
May 12 15:01:49 ns1 named[5570]: zone 1.1.1.in-addr.arpa/IN: sending notifies (serial 133)
May 12 15:01:49 ns1 dhcpd: Added reverse map from 104.1.1.1.in-addr.arpa. to ti7.home.
May 12 15:01:49 ns1 named[5570]: client 1.1.1.3#34042 (1.1.1.in-addr.arpa): transfer of '1.1.1.in-addr.arpa/IN': IXFR started
May 12 15:01:49 ns1 named[5570]: client 1.1.1.3#34042 (1.1.1.in-addr.arpa): transfer of '1.1.1.in-addr.arpa/IN': IXFR ended
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': update unsuccessful: ti7.home: 'name not in use' prerequisite not satisfied (YXDOMAIN)
May 12 15:01:49 ns1 dhcpd: DHCPREQUEST for 1.1.1.103 from c8:f7:33:90:1c:03 via eth0
May 12 15:01:49 ns1 dhcpd: DHCPACK on 1.1.1.103 to c8:f7:33:90:1c:03 (ti7) via eth0
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': update unsuccessful: ti7.home/TXT: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)
May 12 15:01:49 ns1 dhcpd: Forward map from ti7.home. to 1.1.1.103 FAILED: Has an address record but no DHCID, not mine.
May 12 15:01:59 ns1 systemd[1]: Starting Session c31 of user r.
May 12 15:01:59 ns1 systemd[1]: Started Session c31 of user r.
May 12 15:15:09 ns1 dhcpd: DHCPREQUEST for 1.1.1.104 from c8:f7:33:90:1c:03 (ti7) via eth0
May 12 15:15:09 ns1 dhcpd: DHCPACK on 1.1.1.104 to c8:f7:33:90:1c:03 via eth0
May 12 15:15:10 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': update unsuccessful: ti7.home: 'name not in use' prerequisite not satisfied (YXDOMAIN)
May 12 15:15:10 ns1 dhcpd: DHCPREQUEST for 1.1.1.103 from c8:f7:33:90:1c:03 via eth0
May 12 15:15:10 ns1 dhcpd: DHCPACK on 1.1.1.103 to c8:f7:33:90:1c:03 (ti7) via eth0
May 12 15:15:10 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': update unsuccessful: ti7.home/TXT: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)
May 12 15:15:10 ns1 dhcpd: Forward map from ti7.home. to 1.1.1.103 FAILED: Has an address record but no DHCID, not mine.
May 12 15:17:01 ns1 CRON[5697]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 12 15:28:35 ns1 systemd[1]: Starting Session c32 of user r.
May 12 15:28:35 ns1 systemd[1]: Started Session c32 of user r.
May 12 15:42:48 ns1 named[5570]: client 127.0.0.1#57845/key ddns: signer "ddns" approved
May 12 15:42:48 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': adding an RR at 'iPhone.home' A
May 12 15:42:48 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': adding an RR at 'iPhone.home' TXT
May 12 15:42:48 ns1 dhcpd: DHCPREQUEST for 1.1.1.102 from 98:9e:63:66:67:3b via eth0
May 12 15:42:48 ns1 dhcpd: DHCPACK on 1.1.1.102 to 98:9e:63:66:67:3b (iPhone) via eth0
May 12 15:42:48 ns1 named[5570]: zone home/IN: sending notifies (serial 134)
May 12 15:42:48 ns1 dhcpd: Added new forward map from iPhone.home. to 1.1.1.102
May 12 15:42:48 ns1 named[5570]: client 127.0.0.1#57845/key ddns: signer "ddns" approved
May 12 15:42:48 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone '1.1.1.in-addr.arpa/IN': deleting rrset at '102.1.1.1.in-addr.arpa' PTR
May 12 15:42:48 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone '1.1.1.in-addr.arpa/IN': adding an RR at '102.1.1.1.in-addr.arpa' PTR
May 12 15:42:48 ns1 named[5570]: client 1.1.1.3#34576 (home): transfer of 'home/IN': IXFR started
May 12 15:42:48 ns1 named[5570]: client 1.1.1.3#34576 (home): transfer of 'home/IN': IXFR ended
May 12 15:42:48 ns1 dhcpd: Added reverse map from 102.1.1.1.in-addr.arpa. to iPhone.home.
May 12 15:42:48 ns1 named[5570]: zone 1.1.1.in-addr.arpa/IN: sending notifies (serial 134)
May 12 15:42:49 ns1 named[5570]: client 1.1.1.3#46781 (1.1.1.in-addr.arpa): transfer of '1.1.1.in-addr.arpa/IN': IXFR started
May 12 15:42:49 ns1 named[5570]: client 1.1.1.3#46781 (1.1.1.in-addr.arpa): transfer of '1.1.1.in-addr.arpa/IN': IXFR ended



```

I provided some extra lines to show it seems to work, but the essential part is:

```
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': update unsuccessful: ti7.home: 'name not in use' prerequisite not satisfied (YXDOMAIN)
May 12 15:01:49 ns1 dhcpd: DHCPREQUEST for 1.1.1.103 from c8:f7:33:90:1c:03 via eth0
May 12 15:01:49 ns1 dhcpd: DHCPACK on 1.1.1.103 to c8:f7:33:90:1c:03 (ti7) via eth0
May 12 15:01:49 ns1 named[5570]: client 127.0.0.1#57845/key ddns: updating zone 'home/IN': update unsuccessful: ti7.home/TXT: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)
May 12 15:01:49 ns1 dhcpd: Forward map from ti7.home. to 1.1.1.103 FAILED: Has an address record but no DHCID, not mine.
```

But I suspect that this error will go away as long as the device would get 1 IP address, as my first IP is 1.1.1.104, and seeing how those errors regards "my other IP" 1.1.1.103.


Any ideas why I keep getting two IP addresses? I'd appreciate a few pointers!

All the best / R

---

### Post by TheFu on 2018-05-12
Most people will be distracted by the 1.x.x.x subnetting.  I am.

---

### Post by SeijiSensei on 2018-05-12
The DNS stuff is a distraction.  The real question is why is your computer requesting a new address for the same adapter only fifteen minutes after it got the last address.

```

May 12 15:01:49 ns1 dhcpd: DHCPREQUEST for 1.1.1.103 from c8:f7:33:90:1c:03 via eth0
May 12 15:01:49 ns1 dhcpd: DHCPACK on 1.1.1.103 to c8:f7:33:90:1c:03 (ti7) via eth0
May 12 15:15:09 ns1 dhcpd: DHCPREQUEST for 1.1.1.104 from c8:f7:33:90:1c:03 (ti7) via eth0
May 12 15:15:09 ns1 dhcpd: DHCPACK on 1.1.1.104 to c8:f7:33:90:1c:03 via eth0

```

When this happens, does your computer replace the first address with the second?

You could try adding "deny-duplicates" to the global settings in dhcpd.conf along with "one-lease-per-client" that you are using already.

TheFu's comment about your subnet refers to the fact that there are [specific ranges set aside for private networks like yours]("https://tools.ietf.org/html/rfc1918").  You should be using addresses in 10/8, 172.16-32, or 192.168/16.  The address block 1.1.1.0/24 is owned by APNIC, the Asia-Pacific Network Information Center.

```

root@fuzzface:/etc/dhcp# whois 1.1.1.0
% [whois.apnic.net]
% Information related to '1.1.1.0/24AS13335'

route:          1.1.1.0/24
origin:         AS13335
descr:          APNIC Research and Development
                6 Cordelia St
mnt-by:         MAINT-AU-APNIC-GM85-AP
last-modified:  2018-03-16T16:58:06Z
source:         APNIC

```

---

### Post by TheFu on 2018-05-12
Cloudflare runs a privacy-oriented public DNS on 1.1.1.1 and on 1.0.0.1.
[https://www.theverge.com/2018/4/1/17185732/cloudflare-dns-service-1-1-1-1](https://www.theverge.com/2018/4/1/17185732/cloudflare-dns-service-1-1-1-1)

---

### Post by DarkAmbient on 2018-05-12
Hello, thank you for answering.

I know it's a confusing choice of network-address. Been using it for years w/o any issues, guess I've grown accustomed to it, and seeing how it's for _my private lan_, why not. I know about a, b and c class ipv4 network ranges, if you think the issue is due to my setup I'm open to use a standard network one instead.

I tried adding "deny-duplicates" to dhcp.conf, stop the dhcp service, empty /var/lib/dhcp/dhcp.leases* then start it again. 

Upon connecting to the network using client ti7, same result:
```

May 12 23:06:09 ns1 dhcpd: DHCPREQUEST for 1.1.1.104 from c8:f7:33:90:1c:03 via eth0
May 12 23:06:09 ns1 dhcpd: DHCPACK on 1.1.1.104 to c8:f7:33:90:1c:03 (ti7) via eth0
May 12 23:06:09 ns1 dhcpd: Added new forward map from ti7.home. to 1.1.1.104
May 12 23:06:09 ns1 dhcpd: Added reverse map from 104.1.1.1.in-addr.arpa. to ti7.home.
May 12 23:06:09 ns1 dhcpd: DHCPREQUEST for 1.1.1.103 from c8:f7:33:90:1c:03 via eth0
May 12 23:06:09 ns1 dhcpd: DHCPACK on 1.1.1.103 to c8:f7:33:90:1c:03 (ti7) via eth0
May 12 23:06:09 ns1 dhcpd: Forward map from ti7.home. to 1.1.1.103 FAILED: Has an address record but no DHCID, not mine.

```

Might point out that I got no custom settings on the client side.. using the network-manager that tagged along with ubuntu, set to use dhcp.

How it look on the client side:
```

r@ti7:~$ ip a show dev wlp2s0
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether c8:f7:33:90:1c:03 brd ff:ff:ff:ff:ff:ff
    inet 1.1.1.104/24 brd 1.1.1.255 scope global dynamic wlp2s0
       valid_lft 1813167sec preferred_lft 1813167sec
    inet 1.1.1.103/24 brd 1.1.1.255 scope global secondary wlp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::f661:c22c:f103:c43e/64 scope link 
       valid_lft forever preferred_lft forever

```

---

### Post by DarkAmbient on 2018-05-13
I figured out how to stop getting two IP addresses;

After all it was the client at fault, not on the serverside (which I assumed due to new DHCP server).

```

root@ti7:~# systemctl stop dhcpcd
root@ti7:~# systemctl restart network-manager
root@ti7:~# sleep 10 && ip a show dev wlp2s0
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether c8:f7:33:90:1c:03 brd ff:ff:ff:ff:ff:ff
    inet 1.1.1.101/24 brd 1.1.1.255 scope global dynamic wlp2s0
       valid_lft 1813844sec preferred_lft 1813844sec
    inet6 fe80::f661:c22c:f103:c43e/64 scope link 
       valid_lft forever preferred_lft forever

root@ti7:~# systemctl disable dhcpcd
root@ti7:~# host ti7
ti7.home has address 1.1.1.101

```

Not sure why the client got a local dhcp-service, nor why it asked for a second IP here when it doesn't on other networks. 

I'm glad getting rid of the second ip at least, marking this as solved.

---

