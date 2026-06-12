---
title: "Remote Proxy Server"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by NeonSamurai on 2009-06-01
Here's what I'm trying to do:

Use my Xubuntu server as a proxy server at home and as a remote server for my laptop when I use wireless broadband. Basically I want all HTTP traffic going through my server, with the option that if I want to I can use its settings on other remote PC's.

Now I'm having a nightmare trying to get squid configured using advice here:

[Setup a transparent proxy](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

and here:

[Transparent Proxy with Linux](http://tldp.org/HOWTO/TransparentProxy.html)

Here's my squid.conf

> 
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
hosts_file /etc/hosts
refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern . 0 20% 4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl purge method PURGE
acl Safe_ports port 80 # http
acl CONNECT method CONNECT
cache_mem 128 MB
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
acl lan src 192.168.1.1 192.168.2.0/24
http_access allow localhost
http_access allow lan
http_access deny all
http_reply_access allow all
icp_access allow all
visible_hostname myclient.hostname.com
httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on
coredump_dir /var/spool/squid


Now admittedly I've not modified the one I've copied from one of the pages, but it keeps failing saying ports not defined, or not understanding any of the httpd commands. I'm finding a lot of the code lines confusing and not understanding how they relate to my proxy box.

Does anyone have a working squid.conf for a setup similar to the one I'm suggesting that I could look at, or who has an idea of what's missing or incorrect about the one above?

---

### Post by expelledboy on 2009-06-01
Read through [this]("https://help.ubuntu.com/community/Squid").. then do some messing around to get it like you want. I use ebox whenever I want to setup a squid transparent proxy, and my father uses a clarkconnect firewall combo..

Peace out. 8)

---

