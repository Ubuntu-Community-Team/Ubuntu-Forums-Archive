---
title: "Ubuntu with Squid"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Overboardkiller on 2008-04-24
Hey,

I have looked everywhere to help my problem and i don't know what i have done wrong.

I have squid and trying to set up PAM Auth with it. 

Squid works ok with out any auth. I have set up 2 users in ubuntu and also set them up to use webmin as i would like them to reset there passwords. 

```
http_port 8080
#http_port 6789
#http_port 8000
#http_port 9192
icp_port 0
acl QUERY urlpath_regex cgi-bin \?
#acl NOSTREAM dstdomain "/etc/squid/sitenostream"
cache_mem  64 MB
cache_dir ufs /cache/cache 2000 16 256 
cache_access_log /cache/logs/access.log
cache_log /cache/logs/cache.log
cache_store_log /cache/logs/store.log
cache_mgr network.admin@pickles.com.au
cachemgr_passwd password all
logfile_rotate 21
#emulate_httpd_log on
debug_options ALL,2
ftp_user administrator@pickles.com.au
visible_hostname proxy1-DMZB
#authenticate_program /usr/lib/squid/pam_auth
auth_param basic program /usr/lib/squid/pam_auth
auth_param basic children 5
auth_param basic realm Squid Proxy1-DMZB
auth_param basic credentialsttl 2 hours

acl all src 0.0.0.0/0.0.0.0
acl internal src 192.168.0.0/255.255.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl SSL_ports port 443 563
acl Allowed_Ports port 20 21 70 80 210 443 563 8086 8080 1025-65535
acl CONNECT method CONNECT
#acl fullaccess proxy_auth REQUIRED
acl password proxy_auth REQUIRED
#acl sitelocal dstdomain "/etc/squid/sitelocal"
acl grpinoculate src "/etc/squid/grpinoculate"
#acl grpaccounts proxy_auth "/etc/squid/grpaccounts"
#acl siteaccounts dstdomain "/etc/squid/siteaccounts"
#acl grpcars proxy_auth "/etc/squid/grpcars"
#acl sitecars dstdomain "/etc/squid/sitecars"
#acl restrictedusers proxy_auth "/etc/squid/restricteduser"
#acl restricted dstdomain "/etc/squid/restricted"
acl Allstaff proxy_auth "/etc/squid/all"
#no_cache deny QUERY NOSTREAM grpinoculate

#http_access allow manager localhost
#http_access deny manager
#http_access deny !Allowed_Ports
#http_access deny CONNECT !SSL_ports
#http_access allow internal sitelocal
#http_access allow grpinoculate
#http_access allow internal grpaccounts siteaccounts
#http_access allow internal grpcars sitecars
#http_access deny grpaccounts
#http_access deny grpcars
#http_access allow restricted restrictedusers
#http_access allow Allowed_Ports Allstaff
#http_access allow localhost
#http_access allow all
http_access allow Allstaff
http_access deny all

#icp_access deny all

#proxy_auth_realm Pickles Proxy Server
#error_directory /etc/squid/errors
cache_effective_user squid
cache_effective_group squid
#httpd_accel_with_proxy off
#httpd_accel_uses_host_header off

```
Most of the stuff i have commented out as it is not needed and i thought it was causing this error. 

When i try and access the net with firefox i get prompted for a username and password. which i type in correctly and it keeps on asking for password. When i look in the access.log and cache.log this is what i find.

Access.log
```
192.168.1.80 - markw01 [24/Apr/2008:03:43:47 +1000] "GET http://www.bit-tech.net/modding/ HTTP/1.1" 407 1790 TCP_DENIED:NONE
192.168.1.80 - markw01 [24/Apr/2008:03:43:52 +1000] "GET http://www.bit-tech.net/modding/ HTTP/1.1" 407 1790 TCP_DENIED:NONE
192.168.1.80 - markw01 [24/Apr/2008:03:43:57 +1000] "GET http://www.bit-tech.net/modding/ HTTP/1.1" 407 1790 TCP_DENIED:NONE
192.168.1.80 - markw01 [24/Apr/2008:03:44:03 +1000] "GET http://www.bit-tech.net/modding/ HTTP/1.1" 407 1790 TCP_DENIED:NONE
192.168.1.80 - markw01 [24/Apr/2008:03:44:26 +1000] "GET http://www.bit-tech.net/modding/ HTTP/1.1" 407 1790 TCP_DENIED:NONE
```

Cache.log
```
2008/04/24 04:10:24| storeDigestRebuildStart: rebuild #1
2008/04/24 04:10:24| storeDigestCalcCap: have: 25, want 25 entries; limits: [1, 157538]
2008/04/24 04:10:24| storeDigestResize: 157538 -> 25; change: 157513 (100%)
2008/04/24 04:10:24| storeDigestResize: big change, resizing.
2008/04/24 04:10:24| cacheDigestInit: capacity: 25 entries, bpe: 5; size: 16 bytes
2008/04/24 04:10:24| storeDigestRewrite: start rewrite #1
2008/04/24 04:10:24| storeDigestRewriteStart: waiting for rebuild to finish.
2008/04/24 04:10:24| storeDigestRebuildFinish: done.
2008/04/24 04:10:24| storeDigestRewriteFinish: digest expires at 1208977824 (+3600)
2008/04/24 04:10:25| The request GET http://proxy1-dmzb/cgi-bin/chpasswd.cgi is DENIED, because it matched 'Allstaff'
2008/04/24 04:10:25| The reply for GET http://proxy1-dmzb/cgi-bin/chpasswd.cgi is ALLOWED, because it matched 'Allstaff'
2008/04/24 04:10:25| storeLateRelease: released 0 objects
2008/04/24 04:10:26| The request GET http://proxy1-dmzb/favicon.ico is DENIED, because it matched 'Allstaff'
2008/04/24 04:10:26| The reply for GET http://proxy1-dmzb/favicon.ico is ALLOWED, because it matched 'Allstaff'
2008/04/24 04:10:36| The request GET http://news.com.au/ is DENIED, because it matched 'Allstaff'
2008/04/24 04:10:36| The reply for GET http://news.com.au/ is ALLOWED, because it matched 'Allstaff'
2008/04/24 04:10:44| The request GET http://news.com.au/ is DENIED, because it matched 'Allstaff'
2008/04/24 04:10:44| The reply for GET http://news.com.au/ is ALLOWED, because it matched 'Allstaff'
```

I can't see why it is denied and then allowed. I've been working on this for days. I have read so many forums and web pages and none are helping

---

