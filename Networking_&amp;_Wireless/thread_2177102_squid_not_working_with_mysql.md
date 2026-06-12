---
title: "squid not working with mysql"
date: 2013-09-27
forum: Networking &amp; Wireless
---

### Post by anees2 on 2013-09-27
I am using ubuntu 12.04 and centos 6 as virtual machine on it. I've configured squid on centos and I'm trying to access it from browsers in ubuntu.

It worked fine when I used ncsa authentication, but it is not working with mysql db authentication. My squid.conf is 

```
 visible_hostname cenots.assiduzauth_param basic program /usr/lib/squid/squid_db_auth --user authorizer --password watchman --plaintext --persist
auth_param basic children 5
auth_param basic realm Web-Proxy
auth_param basic credentialsttl 1 minute
auth_param basic casesensitive off
#auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/passwd
#auth_param basic children 5
#auth_param basic realm Restricted Area
#auth_param basic realm Squid proxy-caching web server
#auth_param basic credentialsttl 2 hours
#auth_param basic casesensitive on
acl db-auth proxy_auth REQUIRED
http_access allow db-auth
#acl ncsa_users proxy_auth REQUIRED
#http_access allow ncsa_users






acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1


# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
acl localnet src 172.16.0.0/12    # RFC1918 possible internal network
acl localnet src 192.168.0.0/16    # RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines


acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT


#
# Recommended minimum Access Permission configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
http_access deny manager


# Deny requests to certain unsafe ports
http_access deny !Safe_ports


# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports


# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost


#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#


# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
#http_access allow localhost


# And finally deny all other access to this proxy
http_access deny all


# Squid normally listens to port 3128
http_port 8080 transparent


# We recommend you to use at least the following line.
hierarchy_stoplist cgi-bin ?


# Uncomment and adjust the following to add a disk cache directory.
#cache_dir ufs /var/spool/squid 100 16 256


# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid


# Add any of your own refresh_pattern entries above these.
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern .        0    20%    4320


visible_hostname cenots.assiduz
dns_nameservers 8.8.8.8
http_access allow localhost
http_access deny all

```

My access.log file

```
[root@centos ~]# tail /var/log/squid/access.log
1380278085.638      0 192.168.1.3 TCP_DENIED/407 3838 CONNECT versioncheck.addons.mozilla.org:443 - NONE/- text/html
1380278203.901      0 192.168.1.3 TCP_DENIED/403 3514 GET http://weather.noaa.gov/cgi-bin/mgetmetar.pl? - NONE/- text/html
1380278687.977      0 192.168.1.2 TCP_DENIED/407 3975 GET http://networktshooter.info/ - NONE/- text/html
1380278697.832      2 192.168.1.2 TCP_DENIED/407 4083 GET http://networktshooter.info/ anees NONE/- text/html
1380279346.747      1 192.168.1.2 TCP_DENIED/407 3975 GET http://networktshooter.info/ - NONE/- text/html
1380279354.637      3 192.168.1.2 TCP_DENIED/407 4083 GET http://networktshooter.info/ jasir NONE/- text/html
1380279364.612      3 192.168.1.2 TCP_DENIED/407 4083 GET http://networktshooter.info/ anees NONE/- text/html
1380279658.240      1 192.168.1.2 TCP_DENIED/407 3975 GET http://networktshooter.info/ - NONE/- text/html
1380279665.689      3 192.168.1.2 TCP_DENIED/407 4083 GET http://networktshooter.info/ anees NONE/- text/html
1380280003.907      0 192.168.1.3 TCP_DENIED/403 3514 GET http://weather.noaa.gov/cgi-bin/mgetmetar.pl? - NONE/- text/html



```

Here's my cache log file

 ```
[root@centos ~]# tail /var/log/squid/cache.log2013/09/27 16:06:43| Acl.cc(26) AuthenticateAcl:  authentication not applicable on intercepted requests.
DBI connect('database=squid','authorizer',...) failed: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (13) at /usr/lib/squid/squid_db_auth line 127
Could not connect to DBI:mysql:database=squid
DBI connect('database=squid','authorizer',...) failed: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (13) at /usr/lib/squid/squid_db_auth line 127
Could not connect to DBI:mysql:database=squid
DBI connect('database=squid','authorizer',...) failed: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (13) at /usr/lib/squid/squid_db_auth line 127
Could not connect to DBI:mysql:database=squid
DBI connect('database=squid','authorizer',...) failed: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (13) at /usr/lib/squid/squid_db_auth line 127
Could not connect to DBI:mysql:database=squid
2013/09/27 16:36:43| Acl.cc(26) AuthenticateAcl:  authentication not applicable on intercepted requests.



```


Please suggest solutions.

---

### Post by SeijiSensei on 2013-09-27
Is there some reason you need authentication?  The host in the logs is in the 192.168.1.0/24 subnet, so the cache isn't exposed to public Internet.  Can't you just rely on IP-based restrictions?

---

### Post by anees2 on 2013-09-28
> **SeijiSensei said:**
> Is there some reason you need authentication?  The host in the logs is in the 192.168.1.0/24 subnet, so the cache isn't exposed to public Internet.  Can't you just rely on IP-based restrictions?

I am trying to setup authentication with squid proxy server using mysql. I am just testing it. After successful working I need to implement it in an institution. I need to restrict their access, log their access details, provide them opportunity to change their passwords etcc.. using this.

It worked fine when I used ncsa authentication mechanism with squid proxy server, but not working with mysql.

Is the issue with squid or mysql?

---

### Post by SeijiSensei on 2013-09-28
I've never done this, but have you read [http://wiki.squid-cache.org/ConfigExamples/Authenticate/Mysql?](http://wiki.squid-cache.org/ConfigExamples/Authenticate/Mysql?)

I checked the binary with "dpkg -s squid3" and it does have the DB auth mechanism compiled in.

---

### Post by anees2 on 2013-09-29
> **SeijiSensei said:**
> I've never done this, but have you read [http://wiki.squid-cache.org/ConfigExamples/Authenticate/Mysql?](http://wiki.squid-cache.org/ConfigExamples/Authenticate/Mysql?)

I checked the binary with "dpkg -s squid3" and it does have the DB auth mechanism compiled in.


Ok thank you. 

Let me check

---

### Post by anees2 on 2013-09-29
> **anees2 said:**
> Ok thank you. 

Let me check

still not working

---

### Post by SeijiSensei on 2013-09-29
You mean you followed the steps in the Squid wiki entry, and that didn't help?

Have you tried posting on the various Squid [mailing lists]("http://www1.cl.squid-cache.org/Support/mailing-lists.html")?  "Squid-users" is pretty helpful, and even the developers pay attention to it.

---

### Post by anees2 on 2013-09-30
> **SeijiSensei said:**
> You mean you followed the steps in the Squid wiki entry, and that didn't help?

Have you tried posting on the various Squid [mailing lists]("http://www1.cl.squid-cache.org/Support/mailing-lists.html")?  "Squid-users" is pretty helpful, and even the developers pay attention to it.


I followed the steps in Squid wiki entry, it didn't help.

I tried posting in mailing list, but they're rejecting my mail saying it is long. I can't post the conf and log files to them.

Let me try

---

### Post by anees2 on 2013-10-01
The issue is resolved now. The problem was with selinux in CentOS. I've disabled selinux and authentication worked.

Thanks for your replies.

---

