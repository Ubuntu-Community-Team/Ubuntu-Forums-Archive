---
title: "IPTables"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by ricardo22 on 2014-08-26
Hello everyone,

I m mounting a server to be a transparent proxy server with Squid, and i would like to ask a little of help / advice regarding squid or iptables. I compiled squid from the source with the following arguments:

```
#!/bin/sh
'./configure' \
'--build=x86_64-linux-gnu' \
'--srcdir=.' \
'--prefix=/usr' \
'--includedir=/usr/include' \
'--localstatedir=/var' \
'--mandir=/usr/share/man' \
'--infodir=/usr/share/info' \
'--libexecdir=/usr/lib/squid' \
'--datadir=/usr/share/squid' \
'--sysconfdir=/etc/squid' \
'--localstatedir=/var' \
'--bindir=/usr/sbin' \
'--enable-inline' \
'--enable-ssl' \
'--enable-ssl-crtd' \
'--enable-icap-client' \
'--enable-follow-x-forwarded-for' \
'--enable-removal-policies=heap,lru' \
'--enable-delay-pools' \
'--enable-cache-digests' \
'--enable-storeio=ufs,aufs,diskd,rock' \
'--enable-disk-io' \
'--disable-eui' \
'--disable-snmp' \
'--disable-wccp' \
'--disable-wccpv2' \
'--disable-http-violations' \
'--disable-translation' \
'--disable-auto-locale' \
'--disable-htcp' \
'--disable-internal-dns' \
'--with-default-user=proxy' \
'--with-logdir=/var/log/squid/' \
'--with-pidfile=/var/run/squid.pid' \
'--with-filedescriptors=65536' \
'--with-cppunit-basedir=/usr' \
'--with-large-files' \
"$@"
```

and i have the following simple squid.conf

```
http_port 3128
http_port 3129 intercept
https_port 3130 intercept ssl-bump generate-host-certificates=on dynamic_cert_mem_cache_size=8MB cert=/etc/squid/ssl/openssl.crt key=/etc/squid/ssl/openssl.key version=3
visible_hostname proxy.lan

strip_query_terms on
access_log stdio:/var/log/squid/access.log
cache_log /var/log/squid/cache.log

coredump_dir /var/cache/squid
shutdown_lifetime 1 second

ssl_bump server-first all
sslcrtd_program /usr/lib/squid/ssl_crtd -s /etc/squid/ssl/db -M 8MB
sslcrtd_children 5
sslproxy_cert_error allow all
sslproxy_flags DONT_VERIFY_PEER,NO_DEFAULT_CA

acl mydevices src 192.168.1.2 192.168.1.3

http_access allow mydevices
http_access deny all
```

My question/request for help is the following: 
I tried to redirect the port's 80 and 443 initially to the squid intercept port but i learned that to use Intercept i need to do a NAT. So in my main firewall (where someone manages all my 3 networks, and all web traffic get's redirected to to my proxy server) i m m redirecting all traffic from port's 80 and  443 into the proxy server and blocking nearly everything else, and now in the proxy server IPTables i need to do a NAT from the web ports to the squid ports and i tried to do something like this:

```
iptables -P INPUT ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 3128 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 3129 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 3130 -j ACCEPT
iptables -t nat -I PREROUTING -i eth0 ! -s 192.168.1.1 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.1:3129
iptables -t nat -I PREROUTING -i eth0 ! -s 192.168.1.1 -p tcp --dport 443 -j DNAT --to-destination 192.168.1.1:3130
iptables -t nat -I POSTROUTING -p tcp --dport 80 -j MASQUERADE
iptables -t nat -I POSTROUTING -p tcp --dport 443 -j MASQUERADE
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

```

However clients that get the traffic redirected to port 80/443 and iptables redirect them to 3129/3130 are unable to connect to the proxy server (nothing get's logged into squid neither) ... i m not very good with iptables so if anyone could give me a little help i would apreciate it, thanks in advance.

---

### Post by Doug S on 2014-08-27
Hi and welcome to Ubuntu forums,

The squid stuff I know nothing about.

I think you need some forwarding rules in your iptables rule set. As it is right now, nothing will get through. You will need to specifically allow the specific forwarded port traffic through and also have a generic RELATED,ESTABLISHED path through.

Your exact setup is not clear to me (do you have to network interfaces or only one, for example), so it is difficult to provide example iptables FORWARD rules. Just for a test try setting FORWARD default policy to ACCEPT instead of DROP. If that works, we can proceed from there.

Oh, make sure forwarding is enabled.```
echo "1" > /proc/sys/net/ipv4/ip_forward
```And suggest you delete the "iptables -P INPUT ACCEPT" rule, since later on you set it to DROP.

---

### Post by ricardo22 on 2014-08-27
Hello,

Thank for the reply, you are right i forgot to add the environment please forgive me. At this time we have an Firewall on top of all the networks witch manage the incoming/outcoming traffic from all our office and our small "datacenter" (if you can call a machine with VMWARE a datacenter), inside our office we have several vlan's (some for normal PC's and some new ones for Mobile devices) and the idea is to pick the requests from those vlan's on port's 80 and 443 (specially the mobile devices witch dont support proxy configurations) and send them to thee proxy server (using the firewall on top), then the proxy server will translate the normal web ports to the squid port (3128 for normal PC's witch support proxy and 3129 for intercepted DNAT for those who dont support proxy settings ) using IPTables. This Proxy Server is one of the VMWare Virtual machines and at this point only have 1 NIC but i can add more if needed.

Why do i need to do DNAT? because Squid Intercept Mode (if you cannot configure the proxy server like you do in your browser) only allow's to give out the request if they come in by DNAT.

Here's an small diagram:

[IMG]http://i62.tinypic.com/2sax8ix.png[/IMG]

Thanks in advance

---

### Post by SeijiSensei on 2014-08-27
First, I'd drop these commands:

> ```
iptables -t nat -I POSTROUTING -p tcp --dport 80 -j MASQUERADE
iptables -t nat -I POSTROUTING -p tcp --dport 443 -j MASQUERADE
```

There's no need to masquerade traffic to the ports Squid monitors.  Squid acts as a forwarding proxy.  You send it an HTTP request, and it resends the request to the remote server on your behalf.  When it gets a reply it sends it back to you. This works as long as the client and the squid gateway can see each other.

---

### Post by ricardo22 on 2014-08-28
It kinda worked SeijinSensei, however seens like that IPTables is not redirecting the port 80 to 3129 because now i always get connection refused (i see this error in a squid error). Out of curiosity i installed apache2 because he was always saying XXX.XXX.XXX.XXX connection refused where the ip address was the one of my squid machine. After installing apache no mather what URL i placed i was always getting the "It Works!!" web page from apache ... doing the iptables -nL shows the rules are in place how can i be sure that IPtables is working properly?

---

### Post by SeijiSensei on 2014-08-28
For transparent HTTP proxies I use the directive
```
http_port 3128 transparent
```
and route the traffic to 3128 like this:
```
iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 --dport 80
```
Works like a charm.

I'll leave the HTTPS/SSLBump stuff to you.  I looked into it a bit some time ago, but the organization I consult to didn't want to go through the process of adding the required certificates to all the company's browsers.

---

### Post by ricardo22 on 2014-08-29
Hello, the traffic seens to be going through squid but the error maintains the same, i made a clean installation played with a few flags i started to get this on the access.log file:

```
1409310122.877     47 10.0.0.2 TCP_MISS/503 4762 GET http://www.google.pt/ - ORIGINAL_DST/10.1.0.86 text/html
1409310123.218    189 10.0.0.2 TCP_MISS/503 4006 GET http://www.squid-cache.org/Artwork/SN.png - ORIGINAL_DST/10.1.0.86 text/html
1409310123.291      0 10.0.0.2 TCP_MISS/503 4672 GET http://www.google.pt/favicon.ico - ORIGINAL_DST/10.1.0.86 text/html


```

At least the traffic is been redirected witch is a good sign ... also i added the dns_nameservers with the values 8.8.8.8 and 8.8.4.4 to my configuration

---

