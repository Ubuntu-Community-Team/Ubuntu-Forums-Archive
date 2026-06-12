---
title: "Squid configuration"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2014-04-04
this is the version i have to work with
```
root@WZR-300HP:~# squid -v
Squid Cache: Version 3.3.9
configure options:  '--target=mips-linux' '--host=mips-linux' '--prefix=/usr' 'CFLAGS=-Os -pipe -mips32r2 -mtune=mips32r2 -msoft-float  -fno-caller-saves  -mno-branch-likely -DNEED_PRINTF -L/home/seg/DEV/pb42/src/router/openssl' 'CPPFLAGS=-Os -pipe -mips32r2 -mtune=mips32r2 -msoft-float  -fno-caller-saves  -mno-branch-likely -DNEED_PRINTF -L/home/seg/DEV/pb42/src/router/openssl' 'CXXFLAGS=-Os -pipe -mips32r2 -mtune=mips32r2 -msoft-float  -fno-caller-saves  -mno-branch-likely -DNEED_PRINTF -L/home/seg/DEV/pb42/src/router/openssl' 'ac_cv_header_linux_netfilter_ipv4_h=yes' 'ac_cv_epoll_works=yes' '--datadir=/usr/local/squid' '--libexecdir=/usr/lib/squid' '--sysconfdir=/etc/squid' '--enable-shared' '--enable-static' '--enable-x-accelerator-vary' '--with-pthreads' '--with-dl' '--enable-kill-parent-hack' '--enable-arp-acl' '--enable-ssl' '--enable-htcp' '--enable-err-languages=English' '--enable-default-err-language=English' '--enable-linux-netfilter' '--enable-icmp' '--disable-wccp' '--disable-wccpv2' '--disable-snmp' '--disable-htcp' '--enable-underscores' '--enable-cache-digests' '--enable-referer-log' '--enable-delay-pools' '--enable-useragent-log' '--with-openssl=/home/seg/DEV/pb42/src/router/openssl' '--disable-external-acl-helpers' '--disable-auth-negotiate' '--disable-auth-ntlm' '--disable-auth-digest' '--disable-auth-basic' '--enable-epoll' '--with-krb5-config=no' '--with-maxfd=4096' 'host_alias=mips-linux' 'target_alias=mips-linux' 'CC=ccache mips-linux-uclibc-gcc' 'CXX=ccache mips-linux-uclibc-g++' --enable-ltdl-convenience
```
All i want to do i redirect/modify a few URLs based on the domain for all but one system on my lan
i know i need to set the port to port 80 instead of 3128, but i dont know about the rest
i know where my config file is, just don't know what to put in it
since squid is running on my router it sees all the network traffic
so lets say it sees this url
```
http://**us.archive.ubuntu.com**/ubuntu/pool/main/libj/libjpeg6b/libjpeg62-dbg_6b1-3ubuntu1.13.10.1_amd64.deb
```
i want to to change that url to this url
```
 http://**10.0.0.25:3128/us.archive.ubuntu.com**/ubuntu/pool/main/libj/libjpeg6b/libjpeg62-dbg_6b1-3ubuntu1.13.10.1_amd64.deb
```
unless the request came from 10.0.0.25
but if it sees [http://google.com](http://google.com) don't do anything, just let it do what would normally happen

---

### Post by SeijiSensei on 2014-04-04
Are you running squid in "transparent" mode with a corresponding iptables entry?  If so, just add a rule to exempt that specific machine, say 10.0.0.100:
```

iptables -t nat -A PREROUTING -p tcp -s 10.0.0.100 --destination-port 80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --destination-port 80 -j REDIRECT --to-port 3128

```
I don't understand what you are trying to accomplish by "rewriting" the URLs.  Can you be more specific?  I don't think it's something squid can do natively.  What is it about the ubuntu.com site that differentiates it from google.com?

---

### Post by pqwoerituytrueiwoq on 2014-04-04
i want to have the router make any client checking for updates send the request to my apt-cache-ng server, that way i dont have to tell every new install, virtual box, etc. to use it and disable it on mobile hardware when not at home
us.archive.ubuntu.com host the packages, those should be run though the apt-cache-ng server, [www.google.com](www.google.com) is not a package hosting domain soit should not be run though the apt-cache-ng server

---

### Post by SeijiSensei on 2014-04-05
One way to accomplish that is to change the URLs in /etc/apt/sources.list to point to your server.  There are also packages like apt-mirror that are designed to manage a centralized local repository.

---

### Post by pqwoerituytrueiwoq on 2014-04-05
i could just run this command to tell the system to use the local server
```
echo 'Acquire::http { Proxy "http://10.0.0.25:3142"; };' | sudo tee /etc/apt/apt.conf
```
but i don't want to have to run this on every desktop, laptop (would require being disabled when away from home), virtualbox, live session, etc.
If the router sees a request to say us.archive.ubuntu.com it could send it to the proxy that would be better, there should be a way to do that with squid/iptables

I am not going to have the space for apt-mirror, with apt-cache-ng i will have about 5gb of archives at most, this is going to be running on a raspberry pi with a 16gb sd card

---

### Post by Lars Noodén on 2014-04-05
You could try using [always_direct](http://www.squid-cache.org/Doc/config/always_direct/) on an ACL with the site(s) to be skipped and not cached.

---

### Post by pqwoerituytrueiwoq on 2014-04-05
> **Lars Noodén said:**
> You could try using [always_direct]("http://www.squid-cache.org/Doc/config/always_direct/") on an ACL with the site(s) to be skipped and not cached.
is there a opposite version? like always_indirect
i only want to cache a small number of urls
if i were to make a list of direct it would be ever url that exist except about 5 or 6
edit it is in the notes, nrv. i was hoping to use apt-cache-ng since it can remove obsolete packages

---

### Post by SeijiSensei on 2014-04-06
One complicated solution is to run a local DNS server that claims to be authoritative for us.ubuntu.com and gives your server's IP address when queried for archive.us.ubuntu.com.

---

### Post by Lars Noodén on 2014-04-06
> **pqwoerituytrueiwoq said:**
> is there a opposite version? like always_indirect
i only want to cache a small number of urls
if i were to make a list of direct it would be ever url that exist except about 5 or 6
edit it is in the notes, nrv. i was hoping to use apt-cache-ng since it can remove obsolete packages

Then it might be [cache](http://www.squid-cache.org/Doc/config/cache/) that you want.  I'd take a walk through the Squid FAQ and some of the other documentation for ideas:  

[http://wiki.squid-cache.org/Features/StoreUrlRewrite](http://wiki.squid-cache.org/Features/StoreUrlRewrite)
[http://www.squid-cache.org/Doc/config/url_rewrite_program/](http://www.squid-cache.org/Doc/config/url_rewrite_program/)

The rewrite program can be a super simple perl script which then checks for certain addresses and rewrites them to point at apt-cacher.  There are lots of examples online.  I've done short rewriting scripts before, but not recently, and it's not hard to set up.

---

### Post by pqwoerituytrueiwoq on 2014-04-06
> **SeijiSensei said:**
> One complicated solution is to run a local DNS server that claims to be authoritative for us.ubuntu.com and gives your server's IP address when queried for archive.us.ubuntu.com.
i could easily send it like that using dnsmasq, but the proxy needs to know the domain name via url
i think i just found a way to do it with apache2, which i can run on the pi server also
[http://tinyurl.com/l6yb9eu](http://tinyurl.com/l6yb9eu)

---

### Post by SeijiSensei on 2014-04-06
Give the proxy an /etc/hosts file with the correct address.  It will use that in preference to a DNS query.

---

### Post by pqwoerituytrueiwoq on 2014-04-06
> **SeijiSensei said:**
> Give the proxy an /etc/hosts file with the correct address.  It will use that in preference to a DNS query.
thanks, now i don't have to run dnsmasq on the server or force a alt dns server
now i just need the server to get here
:popcorn:

---

### Post by pqwoerituytrueiwoq on 2014-04-13
i am having issues with 3 sources, the rest work
DNSmasq config:
```
address=/archive.canonical.com/10.0.0.25
address=/ppa.launchpad.net/10.0.0.25
address=/archive.getdeb.net/10.0.0.25
```
web server config
```
cat /etc/apache2/sites-available/apt-cacher-ng 
<VirtualHost *:80>
    ServerName apt-cache.local
    ServerAlias us.archive.ubuntu.com security.ubuntu.com archive.canonical.com archive.getdeb.net ppa.launchpad.net extras.ubuntu.com

    ErrorLog /dev/null
    CustomLog /dev/null combined

    RewriteEngine On

    ProxyPreserveHost On

    RewriteRule ^(.*)$ http://127.0.0.1:3142/$1 [L,P]
</VirtualHost>
```

---

