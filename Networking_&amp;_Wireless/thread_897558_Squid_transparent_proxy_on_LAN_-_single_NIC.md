---
title: "Squid transparent proxy on LAN - single NIC"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by steenbras on 2008-08-22
I'm struggling to get a transparent proxy working on my LAN using Squid and iptables. There's loads of documentation out there that helps me to some extent and I can get a squid proxy up and running. I can set it up as a proxy manually in a browser too. But as soon as I try to use it transparently I lose all internet connectivity.

Firstly, the simple topology.

My machine -> WLAN AP -> Switch -> Squid Proxy -> Web Gateway

The squid proxy is an Ubuntu machine running on an old PC, and the web gateway is another old Windows machine connected via USB to a wireless terminal (iBurst). (The web gateway is obviously also connected to the switch, but the topology I show above is how I want traffic to flow.

The squid configuration I have is as follows:

```
http_port 192.168.0.10:3128 transparent
cache_dir ufs /var/spool/squid 500 16 256
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
access_log /var/log/squid/access.log squid
hosts_file /etc/hosts
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
acl lan src 192.168.0.0/24
http_access allow lan
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
cache_effective_group proxy
always_direct allow all
coredump_dir /var/spool/squid

```

The iptables command is:

```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

This is all well and good if I manually set the proxy in my browser preferences, or even if I telnet to the squid proxy (192.168.0.10) on port 80 and do a GET of [http://www.google.com](http://www.google.com). I can see the request in the access.log and also as I'm hitting port 80 it's obvious the iptables redirect is working too.

However, when I test it by dropping the default gateway:
```
sudo route del default
```

and set the squid proxy to be the default gateway:
```
sudo route add default gw 192.168.0.10
```

I lose all internet. I can't ping or browse anything, and nothing shows up in the squid access.log.

Surely it can't be a firewall issue - especially since I can telnet to that machine on port 80? What am I missing?

The other important thing to note is that most of the examples on the web I've found assume a 2 NIC setup for the squid proxy. I don't have that setup - my web gateway is the other Windows machine physically connected via USB to the iBurst terminal.

Please help! I'm getting absolutely nowhere.

My squid is 2.6.STABLE5

---

### Post by steenbras on 2008-08-26
There must be some squid gurus here surely?

---

### Post by jonette20 on 2008-10-15
Hi,

Sorry, I can't tell exactly what is wrong with your file, but it seems that some thing are out of order and I don't know if this matters.

I would suggest that your try out the linuxquestions.org forum and also 
[www.squid-cache.org](www.squid-cache.org).
Those websites were helpful to me when I was setting up my Squid server.

Good Luck

---

