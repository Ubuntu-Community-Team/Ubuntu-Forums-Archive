---
title: "Squid not actually caching anything"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by brockjudkins on 2008-04-02
I have a server running ubuntu 7.10 and the newest squid package installed. I want my Squid to cache objects, not just proxy them, but I seem to only be getting TCP_MISS'es in the access log.

What am I missing?

Here is my /etc/squid/squid.conf (comments removed):

http_port 3128
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
cache_mem 8 MB
maximum_object_size 4096 KB
minimum_object_size 0 KB
maximum_object_size_in_memory 8 KB
cache_replacement_policy heap LFUDA
memory_replacement_policy heap LFUDA
cache_dir ufs /var/spool/squid 2048 16 256
access_log /var/log/squid/access.log squid
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
acl our_networks src 192.168.1.0/24 192.168.2.0/24
http_access allow our_networks
http_access allow localhost
http_access deny all
icp_access allow all
coredump_dir /var/spool/squid
extension_methods REPORT MERGE MKACTIVITY CHECKOUT

---

