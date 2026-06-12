---
title: "Squid Cache Configuration Help"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by spacecoyote on 2008-02-24
I have set up a local squid cache and it works great, but I want it to send **its** requests through another proxy server, running on the same box. This is just a normal proxy server, not a cache, it only has one port, and it doesn't speak Squid, apparently. 

I've looked up how to do this on the Squid website, but it didn't work. I used this code:
```

cache_peer 127.0.0.1 parent 8080 0 no-query
prefer_direct off

```

But Squid just ignores it. The other proxy is a toonel.net java client.

Any help is much appreciated!

---

### Post by spacecoyote on 2008-02-24
**It works!**...mostly. The only thing is that for some reason the transparent proxying doesn't work for the server itself...that is, when I load up a page on the server, it doesn't use the proxy. All other computers do, though. The server is a multipurpose machine and I'd like for the transparent proxying to work for it, too, any help? 

Here's the code:
```

acl apache rep_header Server ^Apache
access_log /var/log/squid/access.log squid
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563      # https, snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443 563     # https, snews
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
http_access allow localhost
acl lan src 192.168.0.0/24
http_access allow localhost
http_access allow lan
http_access deny all
http_reply_access allow all
icp_access allow all
visible_hostname 192.168.0.1
coredump_dir /var/spool/squid
icp_port 0
cache_peer localhost parent 8080 0 default
never_direct allow all

and 

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

```

---

