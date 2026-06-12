---
title: "please correct my squid proxy configuration"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by benquick on 2008-04-03
note:
1 server (installed ubuntu 7.10 desktop edition not server edition), 
ip address eth1  192.168.0.1 connected to hub for gateway
ip address eth0   192.168.1.2, gateway: 192.168.1.254, dns: 202.134.0.155 connected to adsl modem
5 client (installed ubuntu 7.10) ip address: 192.168.0.2 - 192.168.0.6
trouble: squid proxy does't effect, and porn site doesn't blocked, i don't know what wrong with squid configuration, please correct
this is result when i restarting squid
root@bokura:/home/bokura# /etc/init.d/squid restart
* Restarting Squid HTTP proxy squid
*  Waiting...
* ..
* ...                                                                   [ OK ] 
                                                                        [ OK ]
and this is my squid configuration

# NETWORK OPTIONS
# —————————————————————
http_port 3128 transparent
icp_port 0

hierarchy_stoplist cgi-bin ? .js .jsp localhost
acl QUERY urlpath_regex cgi-bin \? .js .jsp localhost
no_cache deny QUERY

# OPTIONS WHICH AFFECT THE CACHE SIZE
# —————————————————————
cache_mem 6 MB
cache_swap_low 98
cache_swap_high 99

maximum_object_size 128 MB
maximum_object_size_in_memory 32 KB

ipcache_size 512
ipcache_low 98
ipcache_high 99
fqdncache_size 256

cache_replacement_policy heap LFUDA
memory_replacement_policy heap GDSF

# LOGFILE PATHNAMES AND CACHE DIRECTORIES
# —————————————————————
cache_dir aufs /var/spool/squid 7000 16 256
logformat squid %tl %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt
access_log /var/log/squid/access.log
cache_log /dev/null
cache_store_log none
mime_table /usr/share/squid/mime.conf
pid_filename /var/run/squid.pid

log_fqdn off
client_netmask 255.255.255.255
ftp_passive on
ftp_sanitycheck on
dns_nameservers 127.0.0.1 202.134.0.155 202.134.2.5

# OPTIONS FOR TUNING THE CACHE
# —————————————————————
refresh_pattern ^ftp: 10080 95% 241920 reload-into-ims override-lastmod
refresh_pattern . 180 95% 120960 reload-into-ims override-lastmod

quick_abort_min 0 KB
quick_abort_max 0 KB
quick_abort_pct 100

negative_ttl 2 minutes
half_closed_clients off
shutdown_lifetime 10 seconds

# ACL CONTROLS
# —————————————————————
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localnet src 192.168.0.0/24
acl server src 192.168.1.0/255.255.255.0
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 777
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
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
acl CONNECT method CONNECT

http_access allow manager all
http_access deny manager
http_access allow localhost
http_access allow localnet
http_access allow server
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny CONNECT
http_access deny all
http_reply_access allow all
icp_access allow all

acl blokporno dstdomain "/etc/squid/pornourl.txt"
http_access deny blokporno
acl keywordblok url_regex -i "/etc/squid/keywordblock.txt"
http_access deny keywordblok
# ADMINISTRATIVE PARAMETERS
# ——————————————————————-
cache_mgr [email]gundalgandil@gmail.com[/email]
visible_hostname server

# DELAY POOL PARAMETERS
# ——————————————————————–

#We don’t want to limit downloads on our local network
acl magic_words1 url_regex -i 192.168.0

#We want to limit downloads of these type of files
acl magic_words2 url_regex -i ftp .exe .mp3 .vqf .tar.gz .gz .rpm .zip .rar .avi .mpeg .mpe .mpg .qt .ram .rm .raw .wav

#We have two different delay_pools
delay_pools 2

#First delay pool
#W don’t want to delay our local traffic
#There are three pool classes; here we will deal only with the second
delay_class 1 2

#-1/-1 mean that there are no limits
delay_parameters 1 -1/-1 -1/-1

#magic_words1: 192.168
delay_access 1 allow magic_words1

#Second delay pool
#we want to delay downloading files mentioned in magic_words2
delay_class 2 2

delay_parameters 2 5000/15000 5000/12000
delay_access 2 allow magic_words2

# MISCELLANEOUS
# ——————————————————————
logfile_rotate 1
memory_pools off
log_icp_queries off
client_db on
query_icmp off
buffered_logs off
reload_into_ims on
header_access Accept-Encoding deny all
nonhierarchical_direct on
prefer_direct off
strip_query_terms off
pipeline_prefetch on
ie_refresh off
forwarded_for off
vary_ignore_expire on

---

### Post by asherlm on 2008-05-07
I'm not a squid master by any means, but here are my thoughts.

> acl blokporno dstdomain "/etc/squid/pornourl.txt"
http_access deny blokporno
acl keywordblok url_regex -i "/etc/squid/keywordblock.txt"
http_access deny keywordblok
You might want to move the http_access deny commands above the > http_access allow localnet line and reload the squid configuration. 

I'm not 100% sure about this, but I think that SQUID reads its acl lists in order and whatever happens to match first is what is allowed. Since the allow localnet command is above the block lists, it will allow any connection out.

---

