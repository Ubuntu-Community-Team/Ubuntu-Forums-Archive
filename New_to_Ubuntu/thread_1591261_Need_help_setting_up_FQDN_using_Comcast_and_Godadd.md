---
title: "Need help setting up FQDN using Comcast and Godaddy"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by LakotaLuna on 2010-10-09
Hello,

I’m trying to build a test box at home and I’m new Ubuntu, DNS and SSH.  I would like to create a fully qualified domain name on my Ubuntu 10.04 computer and get SSH working. I’m having big problems with FQDN and SSH, can’t get them to work. I performing a complete install of Ubuntu from here. I tried to follow the instructions from this article1,this article2 and several other. I replaced “mydomain.com” or “example.com” with “hereismydomain.com” and the IP address with 192.168.1.147 (from Connection Information).  I can’t get pass “Non-authoritative answer” from nslookup.  I’m very confused with which IP addresses to use where and what information to use from GoDaddy and when. After several days I'm about to go crazy. Help would be much appreciated.  Thank you!

Information:
I purchased a domain name from GoDaddy. I’ll call that [www.hereismydomain.com](www.hereismydomain.com), and it has ns51.domaincontrol.com and ns52.domaincontrol.com that resolve to additional IPs.

I have a non-business class Comcast account as my ISP hooked-up to a Linksys router.  The IP address changes (usually back and forth between only two numbers surprisingly, but that may change). On the computer I’m working with this is a snapshot of information from Connection Information and ifconfig:

Auto eth1 (default)
Interface:		Ethernet (eth1)
Hardware Address:	00:0C:F1:9A:E5:E8
Driver:			e100
Speed:			100 Mb/s
Security:			None

IP Address:		192.168.1.147
Broadcast Address:	192.168.1.255
Subnet Mask:		255.255.255.0
Default Route:		192.168.1.1
Primary DNS:		68.87.72.134
Secondary DNS:		68.87.77.134

bigstar@cassiopeia:~$:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:6d:12:87:37  
          inet6 addr: fe80::203:6dff:fe12:8737/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xde00

eth1      Link encap:Ethernet  HWaddr 00:0c:f1:9a:e5:e8  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:47c9:9c8:0:20c:f1ff:fe9a:e5e8/64 Scope:Global
          inet6 addr: fe80::20c:f1ff:fe9a:e5e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5444973 (5.4 MB)  TX bytes:671195 (671.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2237 (2.2 KB)  TX bytes:2237 (2.2 KB)

sudo apt-get install openssh-server
sudo cp /etc/ssh/sshd_config ~
sudo gedit /etc/ssh/sshd_config
  
     ADDED FOLLOWING LINES TO END
     PermitRootLogin no
     AllowUsers USERNAME

Besides updates and installing utilities, here is what I’ve modified and created so far:

bigstar@cassiopeia:~$ sudo cat /etc/bind/named.conf.options
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

	// If your ISP provided one or more IP addresses for stable
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing
	// the all-0's placeholder.

	forwarders {
	 	68.87.72.134;
		68.87.77.134;
	};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

bigstar@cassiopeia:~$ sudo cat /etc/bind/named.conf.local
//
// Do any local configuration here
//
# Our domain zone
zone "hereismydomain.com" {
   type master;
   file "/etc/bind/zones/db.hereismydomain.com";
};

# For reverse DNS
zone "1.168.192.in-addr.arpa" {
   type master;
   notify no;
   file "/etc/bind/db.192";
};

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

bigstar@cassiopeia:~$ sudo cat /etc/bind/zones/db.hereismydomain.com
;
; BIND data file for local loopback interface
;
$TTL	604800
hereismydomain.com.	IN	SOA	ns1.hereismydomain.com. admin.hereismydomain.com. (
		     2010100202		; Serial
			  28800		; Refresh
			   7200		; Retry
			 604800		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns1.hereismydomain.com.
@	IN	NS	ns2.hereismydomain.com.
@	IN	A	192.168.1.147	
@	IN	AAAA	::1
ns	IN	A	192.168.1.147
gw	604800	IN	CNAME	[www.hereismydomain.com](www.hereismydomain.com)
www	604800	IN	CNAME	@
mta	IN	MX	10	mta.hereismydomain.com.
mta	IN	A	192.168.1.147
ns1	IN	A	208.109.225.26
ns2	IN	A	216.69.185.26

;hereismydomain.com.	IN	A	192.168.1.147
;hereismydomain.com.	IN	AAAA	::1
; MX Records
;@	3600	IN	MX	0	smtp.secureserver.net
;@	3600	IN	MX	10	mailstore1.secureserver.net
10	IN	PTR	ns1.hereismydomain.com.
bigstar@cassiopeia:~$
bigstar@cassiopeia:~$ sudo cat /etc/bind/zones/rev.1.168.192.in-addr.arpa
$TTL 3D
@       IN      SOA     ns1.hereismydomain.com. admin.hereismydomain.com. (
                2010100202
                28800
                604800
                604800
                86400
)
            IN      NS      ns1.hereismydomain.com.
            IN      NS      ns2.hereismydomain.com.
147      IN      PTR     ns1.hereismydomain.com.
148      IN      PTR     ns1.hereismydomain.com.

bigstar@cassiopeia:~$

bigstar@cassiopeia:~$ sudo cat /etc/resolv.conf
# Generated by NetworkManager
domain hsd1.il.comcast.net.
search hsd1.il.comcast.net.
nameserver 68.87.72.134
nameserver 68.87.77.134
nameserver 192.168.1.147
bigstar@cassiopeia:~$
bigstar@cassiopeia:~$ dig @localhost hereismydomain.com

; <<>> DiG 9.7.0-P1 <<>> @localhost hereismydomain.com
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65332
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;hereismydomain.com.		IN	A

;; ANSWER SECTION:
hereismydomain.com.	604800	IN	A	192.168.1.147

;; AUTHORITY SECTION:
hereismydomain.com.	604800	IN	NS	ns2.hereismydomain.com.
hereismydomain.com.	604800	IN	NS	ns1.hereismydomain.com.

;; ADDITIONAL SECTION:
ns1.hereismydomain.com.	604800	IN	A	208.109.225.26
ns2.hereismydomain.com.	604800	IN	A	216.69.185.26

;; Query time: 0 msec
;; SERVER: ::1#53(::1)
;; WHEN: Sat Oct  9 00:05:25 2010
;; MSG SIZE  rcvd: 119

bigstar@cassiopeia:~$

bigstar@cassiopeia:~$ dig hereismydomain.com

; <<>> DiG 9.7.0-P1 <<>> hereismydomain.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61377
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;hereismydomain.com.		IN	A

;; ANSWER SECTION:
hereismydomain.com.	3503	IN	A	68.178.232.100

;; Query time: 12 msec
;; SERVER: 68.87.72.134#53(68.87.72.134)
;; WHEN: Sat Oct  9 00:07:30 2010
;; MSG SIZE  rcvd: 51

bigstar@cassiopeia:~$
bigstar@cassiopeia:~$ nslookup hereismydomain.com
Server:		68.87.72.134
Address:	68.87.72.134#53

Non-authoritative answer:
Name:	hereismydomain.com
Address: 68.178.232.100

---

