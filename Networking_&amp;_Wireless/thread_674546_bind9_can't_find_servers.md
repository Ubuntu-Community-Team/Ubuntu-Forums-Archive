---
title: "bind9 can't find servers"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by bturrie on 2008-01-21
I've been trying to get bind9 working in my xubuntu feisty system. It was working as a recursive dns, but isn't now that it tried to make it authoritative.

my zone files are in /etc/bind/zones and look like:

@	IN	SOA	goldenbraid.turrie.com. bturrie.yahoo.com. (
			 2008012001		; Serial
			 3600		; Refresh
			 432000		; Expire
			 38400 )	; Negative Cache TTL
turrie.com.	IN	NS	goldenbraid.turrie.com.
turrie.com.	IN	NS	pdc1.turrie.com.
goldenbraid	IN	A	192.168.1.8
pdc1	IN	A	192.168.1.7
apachex	IN	A	192.168.1.5

for the forward direction and :

@	IN	SOA	goldenbraid.turrie.com. bturrie.yahoo.com. (
			 2008012001		; Serial
			 3600		; Refresh
			 432000		; Expire
			 38400 )	; Negative Cache TTL
	turrie.com.	IN	NS	goldenbraid.turrie.com.
	turrie.com.	IN	NS	pdc1.turrie.com.
	8	IN	PTR	goldenbraid.turrie.com.	
	7	IN	PTR	pdc1.turrie.com.	
	5	IN	PTR	apachex.turrie.com.

for the reverse direction

my named.local file has

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone 	"turrie.com" {
	type master;
	file "/etc/bind/zones/turrie.com.hosts";
	};
zone 	"1.168.192.in-addr.arpa" {
	type master;
	file "/etc/bind/zones/192.168.1.hosts";
	};

when i try:

bruce@goldenbraid:~$ nslookup goldenbraid.turrie.com. 192.168.1.8

i get

Server:         192.168.1.8
Address:        192.168.1.8#53

** server can't find goldenbraid.turrie.com: SERVFAIL

The reverse look is similar

bruce@goldenbraid:~$ nslookup 192.168.1.5 192.168.1.8
Server:         192.168.1.8
Address:        192.168.1.8#53

** server can't find 5.1.168.192.in-addr.arpa: SERVFAIL

something is clearly wrong with my configuration but i don't see what. I have tried reloading bind to no avail. what am i missing here???

---

### Post by kirsche on 2008-01-22
have a look in the log of bind - it might report an error there.
Also, just in case, try with another "dummy" zone...
[http://pgl.yoyo.org/adservers/bind-zone-file-creator.php](http://pgl.yoyo.org/adservers/bind-zone-file-creator.php)

---

### Post by bturrie on 2008-01-24
When I reload bibd9 I get this in the daemon.log file

Jan 24 19:15:19 goldenbraid named[4399]: zone 1.168.192.in-addr.arpa/IN: loading master file /etc/bind/zones/192.168.1.hosts: unknown class/type
Jan 24 19:15:19 goldenbraid named[4399]: /etc/bind/zones/turrie.com.hosts:1: unknown RR type 'version='
Jan 24 19:15:19 goldenbraid named[4399]: zone turrie.com/IN: loading master file /etc/bind/zones/turrie.com.hosts: unknown class/type

---

### Post by bturrie on 2008-01-28
I knew when I posted this that it something odd was going on, odd and perhaps stupid. As it turns out that was correct, I was using Abiword (an Xubuntu word processor) to create my configuration files. Abiword was adding hidden text to the file that was confusing bind9. When I entered the same stuff with Gtkedit it worked fine.

---

