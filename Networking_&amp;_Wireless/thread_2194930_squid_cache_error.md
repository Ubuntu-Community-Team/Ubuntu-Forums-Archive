---
title: "squid cache error"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by denbagoos on 2013-12-21
hi,i'm new about ubuntu and squid and a wanna ask about them
i build external proxy using ubuntu 10.04 and lusca
cpu spec :
[COLOR=#333333][FONT=Trebuchet MS]1. AMD Athlon(tm) II X2 215[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]2. 2 HDD 160gb (system) dan 250 GB (cache)[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]3. RAM 4GB

[/FONT][/COLOR]squid.conf
```

#=======================================================================#
## SQUID - Youtube Cache Super Squid Proxy
## [http://www.indoit.web.id/2012/04/youtube-cache-super-squid-proxy.html](http://www.indoit.web.id/2012/04/youtube-cache-super-squid-proxy.html)
##======================================================================#
## Updated:    20 April 2012 | IndoIT.web.id
## [http://www.indoit.web.id](http://www.indoit.web.id)
#=======================================================================#


http_port 3128 transparent
server_http11 on


pid_filename /var/run/squid.pid
coredump_dir /var/spool/squid/
error_directory /usr/share/squid/errors/English
icon_directory /usr/share/squid/icons
mime_table /usr/share/squid/mime.conf


cache_mem 8 MB
maximum_object_size_in_memory 512 bytes
memory_replacement_policy heap GDSF
cache_replacement_policy heap LFUDA


minimum_object_size 0 KB
maximum_object_size 512 MB
cache_swap_low 97
cache_swap_high 99


cache_dir aufs /cache1 100000 235 256 
cache_dir aufs /cache2 100000 235 256 


# cache_dir aufs /cache 12000 28 256


access_log daemon:/var/log/squid/access.log squid
cache_log /var/log/squid/cache.log
cache_store_log none
store_dir_select_algorithm  round-robin
logfile_daemon /usr/lib/squid/logfile-daemon
logfile_rotate 1


acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 192.168.0.0/24 # RFC1918 possible internal network
acl localnet src 192.168.1.0/24 # RFC1918 possible internal network
acl localnet src 192.168.3.0/24 # RFC1918 possible internal network
acl localnet src 192.168.4.0/24 # RFC1918 possible internal network
acl localnet src 192.168.5.0/24 # RFC1918 possible internal network


acl NO-CACHE-SITES dstdomain "/etc/squid/not-to-cache-sites.txt"
#no_cache deny NO-CACHE-SITES


acl SSL_ports port 443
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
acl purge method PURGE
acl snmppublic snmp_community public
include /usr/local/share/squid/supercache.conf






icp_access allow localnet
icp_access deny all
icp_port 0


buffered_logs on


acl shoutcast rep_header X-HTTP09-First-Line ^ICY.[0-9]
upgrade_http0.9 deny shoutcast


acl apache rep_header Server ^Apache
broken_vary_encoding allow apache


forwarded_for off
header_access From deny all
header_access Server deny all
header_access Link deny all
header_access Via deny all
header_access X-Forwarded-For deny all
httpd_suppress_version_string on


shutdown_lifetime 10 second


snmp_port 3401
snmp_access allow snmppublic all
dns_timeout 1 minutes


#dns_nameservers 8.8.8.8
#dns_testnames 127.0.0.1


#fqdncache_size 4096        # aslinya
fqdncache_size 16384
#ipcache_size 10240        # aslinya
ipcache_size 16384
ipcache_low 97
ipcache_high 99
log_fqdn off
memory_pools off


maximum_single_addr_tries 2
retry_on_error on


icp_hit_stale on


strip_query_terms off
strip_query_terms off
acl yutub url_regex -i .*youtube\.com\/.*$
acl yutub url_regex -i .*youtu\.be\/.*$
logformat squid1 %{Referer}>h %ru
access_log /var/log/squid/yt.log squid1 yutub
acl redirec urlpath_regex -i .*&redirect_counter=1&cms_redirect=yes
acl redirec urlpath_regex -i .*&ir=1&rr=12
acl reddeny url_regex -i c\.youtube\.com\/videoplayback.*redirect_counter=1.*$
acl reddeny url_regex -i c\.youtube\.com\/videoplayback.*cms_redirect=yes.*$
acl block-site dstdom_regex download.windowsupdate.com
http_access deny block-site
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access allow all
http_access deny all
cache deny NO-CACHE-SITES redirec
storeurl_access deny reddeny


query_icmp on
reload_into_ims on
emulate_httpd_log off
negative_ttl 0 second
pipeline_prefetch on
vary_ignore_expire on
half_closed_clients off
high_page_fault_warning 2
nonhierarchical_direct on
prefer_direct off
cache_mgr [EMAIL="denbagoos@gmail.com"]denbagoos@gmail.com[/EMAIL]
cache_effective_user proxy
cache_effective_group proxy
visible_hostname proxy.drain.net
unique_hostname indoit.web.id
cachemgr_passwd none all
client_db on
max_filedescriptors 8192


# TAG: ZPH
zph_mode tos
zph_local 0x30
zph_parent 0
zph_option 136

```


supercache.conf
```

acl store_rewrite_list urlpath_regex \/(get_video|video\?v|videoplayback\?id|videoplayback.*id)
acl store_rewrite_list urlpath_regex \/(get_video\?|videodownload\?|videoplayback.*id|watch\?)
acl store_rewrite_list urlpath_regex \.(3gp|mp(3|4)|flv|(m|f)4v|on2|fid|avi|mov|wm(a|v)|(mp(e?g|a|e|1|2))|mk(a|v)|jp(e?g|e|2)|gif|png|tiff?|bmp|tga|svg|ico|swf|exe|ms(i|u|p)|cab|psf|mar|bin|z(ip|[0-9]{2})|r(ar|[0-9]{2})|7z)\?
acl store_rewrite_list_domain url_regex ^http:\/\/(([a-z-]+[0-9-]+)|([0-9-]+[a-z-]+))\.[a-z0-9-]*\.[a-z]{2,4}
acl store_rewrite_list_domain url_regex ^http:\/\/([a-zA-Z-]+[0-9-]+)\.[A-Za-z]*\.[A-Za-z]*
acl store_rewrite_list_domain url_regex (([a-z]{1,2}[0-9]{1,3})|([0-9]{1,3}[a-z]{1,2}))\.[a-z]*[0-9]?\.[a-z]{3}
acl store_rewrite_list_path urlpath_regex \.(3gp|mp(3|4)|flv|(m|f)4v|on2|fid|avi|mov|wm(a|v)|(mp(e?g|a|e|1|2))|mk(a|v)|jp(e?g|e|2)|gif|png|tiff?|bmp|tga|svg|ico|swf|exe|ms(i|u|p)|cab|psf|mar|bin|z(ip|[0-9]{2})|r(ar|[0-9]{2})|7z)$
acl store_rewrite_list_domain_CDN url_regex (cbk|mt|khm|mlt|tbn)[0-9]?.google\.co(m|\.uk|\.id)
acl store_rewrite_list_domain_CDN url_regex photos-[a-z].ak.fbcdn.net
acl store_rewrite_list_domain_CDN url_regex ^http:\/\/([a-z])[0-9]?(\.gstatic\.com|\.wikimapia\.org)
acl store_rewrite_list_domain_CDN url_regex ^http:\/\/[.a-z0-9]*\.photobucket\.com.*\.[a-z]{3}$
#acl store_rewrite_list_domain_CDN url_regex ^http:\/\/.*speedtest.*
acl store_rewrite_list_domain_CDN url_regex streamate.doublepimp.com.*\.js\? \.doubleclick\.net.* yieldmanager cpxinteractive  quantserve\.com
acl speedtest_allow_url url_regex -i \.speedtest\.net\/ speedtest
acl speedtest_allow_url url_regex ^http:\/\/speedtest\.*
acl speedtest_allow_dom dstdomain .speedtest.net


acl dontrewrite url_regex (get_video|video\?v=|videoplayback\?id|videoplayback.*id).*begin\=[1-9][0-9]* \.php\? \.asp\? \.aspx\? threadless.*\.jpg\?r=
acl getmethod method GET


storeurl_access deny dontrewrite
storeurl_access deny !getmethod


storeurl_access allow store_rewrite_list_domain_CDN
storeurl_access allow store_rewrite_list
storeurl_access allow store_rewrite_list_domain store_rewrite_list_path
storeurl_access allow speedtest_allow_url
storeurl_access allow speedtest_allow_dom
storeurl_access deny all
storeurl_rewrite_program /usr/local/share/squid/supercache.pl
#storeurl_rewrite_children 1
storeurl_rewrite_children 4
#storeurl_rewrite_concurrency 99
storeurl_rewrite_concurrency 10


acl DENYCACHE urlpath_regex \.(ini|ui|lst|inf|pak|ver|patch|md5|cfg|lst|list|rsc|log|conf|dbd|db)$
acl DENYCACHE urlpath_regex (notice.html|afs.dat|dat.asp|patchinfo.xml|version.list|iepngfix.htc|updates.txt|patchlist.txt)
acl DENYCACHE urlpath_regex (pointblank.css|login_form.css|form.css)$
acl DENYCACHE urlpath_regex (Loader|gamenotice|sources|captcha|notice|reset)
cache deny DENYCACHE


refresh_pattern \.facebook\.com.*\.(jp(e?g|e|2)|gif|png|tiff?|bmp|swf|mp(4|3)) 43800 99999% 43200 override-expire ignore-reload ignore-no-cache ignore-private ignore-no-store ignore-must-revalidate store-stale
refresh_pattern \.fbcdn\.net.*\.(jp(e?g|e|2)|gif|png|tiff?|bmp|swf|mp(4|3))  43800 99999% 43800 override-expire ignore-reload ignore-no-cache ignore-private ignore-no-store ignore-must-revalidate store-stale negative-ttl=0
refresh_pattern ^.*safebrowsing.*google 2629742 999999% 2629742 override-expire ignore-reload ignore-no-cache ignore-no-store ignore-private ignore-auth ignore-must-revalidate negative-ttl=10080 store-stale


#ads
refresh_pattern ^.*(streamate.doublepimp.com.*\.js\?|utm\.gif|ads\?|rmxads\.com|ad\.z5x\.net|bh\.contextweb\.com|bstats\.adbrite\.com|a1\.interclick\.com|ad\.trafficmp\.com|ads\.cubics\.com|ad\.xtendmedia\.com|\.googlesyndication\.com|advertising\.com|yieldmanager|game-advertising\.com|pixel\.quantserve\.com|adperium\.com|doubleclick\.net|adserving\.cpxinteractive\.com|syndication\.com|media.fastclick.net).* 2629742 20% 2629742 ignore-no-cache ignore-no-store ignore-private override-expire ignore-reload ignore-auth ignore-must-revalidate store-stale negative-ttl=40320 max-stale=1440


refresh_pattern (get_video\?|videoplayback\?|videodownload\?|watch\?\.flv?|.vid\?) 2629742 99999999% 2629742 override-expire ignore-reload ignore-must-revalidate ignore-no-cache ignore-no-store ignore-private store-stale negative-ttl=0
refresh_pattern (\.swf\?|\.avi\?|\.mov\?|\.wm(a|v)\?|\.3gp\?|\.mp(4|3)\?|\.rm\?|\.ram\?|\.m4v\?|\.on2\?) 43200 999999% 2629742 override-expire ignore-reload ignore-must-revalidate ignore-no-cache ignore-no-store ignore-private store-stale negative-ttl=0
refresh_pattern \.(ico|video-stats) 2629742 999999% 2629742 override-expire ignore-reload ignore-no-cache ignore-no-store ignore-private ignore-auth override-lastmod ignore-must-revalidate negative-ttl=10080 store-stale


refresh_pattern (photobucket|pbsrc|flickr|yimg|ytimg|twimg|gravatar)\.com.*\.(jp(e?g|e|2)|gif|png|tiff?|bmp|swf|mp(4|3)) 2629742 999999% 2629742 override-expire ignore-reload ignore-no-cache ignore-private ignore-no-store ignore-must-revalidate store-stale
refresh_pattern ^http:\/\/images|image|img|pics|openx|thumbs[0-9]\. 2629742 999999% 2629742 override-expire ignore-reload ignore-no-cache ignore-private ignore-no-store ignore-must-revalidate store-stale
refresh_pattern (zynga|ninjasaga|mafiawars|cityville|farmville|crowdstar|spilcdn|agame|popcap)\.com/.* 2629742 999999% 2629742 override-expire ignore-reload ignore-no-cache ignore-private ignore-no-store ignore-must-revalidate store-stale
refresh_pattern \.(akamaihd|edgecastcdn|spilcdn|zgncdn|(tw|y|yt)img)\.com.*\.(jp(e?g|e|2)|gif|png|swf|mp(3|4)) 43200 99999% 43200 override-expire override-lastmod ignore-reload ignore-no-cache ignore-private ignore-must-revalidate store-stale
refresh_pattern \.gstatic\.com/images\? 43200 99999% 43200 override-expire override-lastmod ignore-reload ignore-no-cache ignore-private ignore-must-revalidate store-stale
refresh_pattern (gstatic|diggstatic)\.com/.* 2629742 999999% 2629742 override-expire ignore-reload ignore-no-cache ignore-private ignore-no-store ignore-must-revalidate store-stale
refresh_pattern ^[http://((cbk|mt|khm|mlt|tbn](http://((cbk|mt|khm|mlt|tbn))[0-9]?)\.google\.co(m|\.uk|\.id) 43200 999999% 43200 override-expire override-lastmod ignore-reload ignore-no-cache ignore-private ignore-auth ignore-must-revalidate ignore-no-store negative-ttl=10080 store-stale 
refresh_pattern vid\.akm\.dailymotion\.com.*\.on2\? 2629742 999999% 2629742 ignore-no-cache override-expire override-lastmod store-stale
refresh_pattern \.speedtest/.* 43200 99999% 432000 override-expire ignore-reload ignore-no-cache ignore-no-store ignore-must-revalidate store-stale
refresh_pattern galleries\.video(\?|sz) 2629742 999999% 2629742 override-expire ignore-reload ignore-no-cache ignore-must-revalidate ignore-private store-stale
refresh_pattern \.wikimapia\.org\/? 43200 99999% 43200 override-expire override-lastmod ignore-reload ignore-no-cache ignore-private ignore-must-revalidate store-stale
refresh_pattern \.(rackcdn|spilcdn|zgncdn)\.com.*\.(jp(e?g|e|2)|gif|png|swf|mp(3|4)) 43200 9999% 43200 override-expire ignore-reload ignore-no-cache store-stale
refresh_pattern code.googlec.com.*(svn|download) 0 50% 1440 reload-into-ims


#sensitive site
refresh_pattern -i \.(sc-|dl-|ex-|mh-|dll|da-|iop) 0 5% 60 reload-into-ims
refresh_pattern -i \.(mst|Xtp)$ 0 50% 1440 reload-into-ims
refresh_pattern -i (main.exe|update.exe|grandchase.exe|FSLauncher.exe|FreeStyle_Setup.exe|grandchase.exe|filelist.zip|autoupgrade.exe)$ 0 50% 1440 reload-into-ims
refresh_pattern -i (UpdaterModifier.exe|FreeStyle.exe|PBLauncher.exe|update.exe|NewLauncher.exe|NewAvalon.exe|hon.exe.zip|cabal.exe)$ 0 50% 1440 reload-into-ims
refresh_pattern -i (PointBlank.exe.zip|HSUpdate.exe.zip|PBConfig.exe.zip) 0 50% 1440 reload-into-ims
refresh_pattern -i (wks_avira-win32-en-pecl.info.gz|wks_avira10-win32-en-pecl.info.gz)$ 0 50% 1440 reload-into-ims
refresh_pattern -i (setup.exe.gz|avscan.exe.gz|avguard.exe.gz|filelist.zip|AvaClient.exe) 0 50% 1440 reload-into-ims
refresh_pattern -i (livescore.com|goal.com|bobet) 0 50% 60 reload-into-ims


#antivirus
refresh_pattern avast.com.*\.vpx 40320 90% 161280 ignore-reload ignore-no-cache ignore-no-store store-stale ignore-must-revalidate reload-into-ims
refresh_pattern (avgate|avira).*\.(idx|gz)$ 1440 90% 1440 ignore-reload ignore-no-cache ignore-no-store store-stale ignore-must-revalidate 
refresh_pattern kaspersky.*\.avc$ 2629742 999999% 2629742 ignore-reload store-stale
refresh_pattern kaspersky 1440 50% 161280 ignore-no-cache store-stale


#general
refresh_pattern \.(jp(e?g|e|2)|tiff?|bmp|gif|png) 2629742 999999% 2629742 ignore-no-cache ignore-no-store reload-into-ims override-expire ignore-private  ignore-must-revalidate store-stale
refresh_pattern \.(z(ip|[0-9]{2})|r(ar|[0-9]{2})|jar|bz2|gz|tar|rpm|vpu) 2629742 999999% 2629742 override-expire reload-into-ims ignore-no-cache ignore-private ignore-must-revalidate ignore-no-store store-stale
refresh_pattern \.(mp3|wav|og(g|a)|flac|midi?|rm|aac|wma|mka|ape) 2629742 999999% 2629742 override-expire reload-into-ims ignore-reload ignore-no-cache ignore-private ignore-must-revalidate ignore-no-store store-stale
refresh_pattern \.(exe|msi|msp|msu|dmg|bin|xpi|iso|swf|mar|psf|cab) 2629742 999999% 2629742 override-expire reload-into-ims ignore-reload ignore-no-cache ignore-private ignore-must-revalidate ignore-no-store store-stale
refresh_pattern \.(mpeg|ra?m|avi|mp(g|e|4)|mov|divx|asf|wmv|m\dv|rv|vob|asx|ogm|flv|3gp|on2) 2629742 999999% 2629742 override-expire override-lastmod ignore-reload ignore-no-cache ignore-private ignore-auth ignore-must-revalidate ignore-no-store negative-ttl=0 store-stale
refresh_pattern -i (cgi-bin) 0 0% 0
refresh_pattern \.(php|jsp|cgi|asx|asp|aspx)\? 0 0% 0
refresh_pattern ^ftp: 40320 20% 40320 override-expire reload-into-ims store-stale
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern . 0 50% 40320  store-stale

```


supercache.pl
```

#!/usr/bin/perl


# ISI DARI STOREURL DIBAWAH INI GADO GADO.
# ADA YG DARI CHUDY DAN ADA YG DARI SHUDY
# SHUDYLAH BERBAGI ILMU :3
# ucok_karnadi(at)yahoo.com or [https://twitter.com/syaifuddin_jw](https://twitter.com/syaifuddin_jw)


$|=1;
while (<>) {
@X = split;
$x = $X[0] . " ";


#facebook
if (m/^http\:\/\/.*(profile|photo).*\.ak\.fbcdn\.net(\/h(profile|photos)-ak-)(snc|ash|prn)[0-9]?(.*)/) {
print $x . "http://facebook.SQUIDINTERNAL" . $2 . "fb" . $5 . "\n";


#Speedtest
} elsif (m/^http\:\/\/.*\/speedtest\/(.*)\?.*/) {
print $x . "http://speedtest.SQUIDINTERNAL/speedtest/" . $1 . "\n";


#reverbnation
} elsif (m/^http:\/\/[a-z0-9]{4}\.reverbnation\.com\/.*\/([0-9]*).*/) {
print $x . "http://reverbnation.com.SQUIDINTERNAL/" . "$1" . "\n";


#BLOGSPOT
} elsif (m/^http:\/\/[1-4].bp.(blogspot.com.*)/) {
print $x . "http://blog-cdn." . $1 . "\n";


#ytimg
} elsif (m/^http:\/\/i[1-4]\.ytimg\.com(.*)/) {
print $x . "http://cdn.ytimg.com" . $1 . "\n";


#AVAST
} elsif (m/^http:\/\/download[0-9]{3}.(avast.com.*)/) {
print $x . "http://avast-cdn." . $1 . "\n";


#KAV
} elsif (m/^http:\/\/dnl-[0-9]{2}.(geo.kaspersky.com.*)/) {
print $x . "http://kav-cdn." . $1 . "\n";


#AVG
} elsif (m/^http:\/\/update.avg.com/) {
print $x . "http://avg-cdn." . $1 . "\n";


#maps.google.com
} elsif (m/^http:\/\/(cbk|mt|khm|mlt|tbn)[0-9]?(.google\.co(m|\.uk|\.id).*)/) {
print $x . "http://" . $1 . $2 . "\n";


#gstatic and/or wikimapia
} elsif (m/^http:\/\/([a-z])[0-9]?(\.gstatic\.com.*|\.wikimapia\.org.*)/) {
print $x . "http://" . $1 . $2 . "\n";


#maps.google.com
} elsif (m/^http:\/\/(khm|mt)[0-9]?(.google.com.*)/) {
print $x . "http://" . $1 . $2 . "\n";


# for ALL Youtube ( range & non range )
# first you need do this
# install package dependencies "apt-get install libfile-readbackwards-perl"
# add line below to your squid config and remove "#"


# strip_query_terms off
# acl yutub url_regex -i .*youtube\.com\/.*$
# acl yutub url_regex -i .*youtu\.be\/.*$
# logformat squid1 %{Referer}>h %ru
# access_log /var/log/squid/yt.log squid1 yutub
# acl redirec urlpath_regex -i .*&redirect_counter=1&cms_redirect=yes
# acl redirec urlpath_regex -i .*&ir=1&rr=12
# cache deny redirec
# acl reddeny url_regex -i c\.youtube\.com\/videoplayback.*redirect_counter=1.*$
# acl reddeny url_regex -i c\.youtube\.com\/videoplayback.*cms_redirect=yes.*$
# storeurl_access deny reddeny


} elsif ($X[1] =~ m/^http\:\/\/.*(youtube|google).*videoplayback.*/){
@itag = m/[&?](itag=[0-9]*)/;
@CPN = m/[&?]cpn\=([a-zA-Z0-9\-\_]*)/;
@IDS = m/[&?]id\=([a-zA-Z0-9\-\_]*)/;
$id = &GetID($CPN[0], $IDS[0]);
@range = m/[&?](range=[^\&\s]*)/;
print $x . "http://video-srv.youtube.com.SQUIDINTERNAL/id=" . $id . "&@itag@range\n";;


#Google
} elsif (m/^http:\/\/www\.google-analytics\.com\/__utm\.gif\?.*/) {
print $x . "http://www.google-analytics.com/__utm.gif\n";


#Cache High Latency Ads
} elsif (m/^http:\/\/([a-z0-9.]*)(\.doubleclick\.net|\.quantserve\.com|\.googlesyndication\.com|yieldmanager|cpxinteractive)(.*)/) {
$y = $3;$z = $2;
for ($y) {
s/pixel;.*/pixel/;
s/activity;.*/activity/;
s/(imgad[^&]*).*/\1/;
s/;ord=[?0-9]*//;
s/;&timestamp=[0-9]*//;
s/[&?]correlator=[0-9]*//;
s/&cookie=[^&]*//;
s/&ga_hid=[^&]*//;
s/&ga_vid=[^&]*//;
s/&ga_sid=[^&]*//;
# s/&prev_slotnames=[^&]*//
# s/&u_his=[^&]*//;
s/&dt=[^&]*//;
s/&dtd=[^&]*//;
s/&lmt=[^&]*//;
s/(&alternate_ad_url=http%3A%2F%2F[^(%2F)]*)[^&]*/\1/;
s/(&url=http%3A%2F%2F[^(%2F)]*)[^&]*/\1/;
s/(&ref=http%3A%2F%2F[^(%2F)]*)[^&]*/\1/;
s/(&cookie=http%3A%2F%2F[^(%2F)]*)[^&]*/\1/;
s/[;&?]ord=[?0-9]*//;
s/[;&]mpvid=[^&;]*//;
s/&xpc=[^&]*//;
# yieldmanager
s/\?clickTag=[^&]*//;
s/&u=[^&]*//;
s/&slotname=[^&]*//;
s/&page_slots=[^&]*//;
}
print $x . "http://" . $1 . $2 . $y . "\n";


#cache high latency ads
} elsif (m/^http:\/\/(.*?)\/(ads)\?(.*?)/) {
print $x . "http://" . $1 . "/" . $2 . "\n";


} elsif (m/^http:\/\/(www\.ziddu\.com.*\.[^\/]{3,4})\/(.*?)/) {
print $x . "http://" . $1 . "\n";


#cdn, varialble 1st path
} elsif (($X[1] =~ /filehippo/) && (m/^http:\/\/(.*?)\.(.*?)\/(.*?)\/(.*)\.([a-z0-9]{3,4})(\?.*)?/)) {
@y = ($1,$2,$4,$5);
$y[0] =~ s/[a-z0-9]{2,5}/cdn./;
print $x . "http://" . $y[0] . $y[1] . "/" . $y[2] . "." . $y[3] . "\n";


#rapidshare
} elsif (($X[1] =~ /rapidshare/) && (m/^http:\/\/(([A-Za-z]+[0-9-.]+)*?)([a-z]*\.[^\/]{3}\/[a-z]*\/[0-9]*)\/(.*?)\/([^\/\?\&]{4,})$/)) {
print $x . "http://cdn." . $3 . "/SQUIDINTERNAL/" . $5 . "\n";


} elsif (($X[1] =~ /maxporn/) && (m/^http:\/\/([^\/]*?)\/(.*?)\/([^\/]*?)(\?.*)?$/)) {
print $x . "http://" . $1 . "/SQUIDINTERNAL/" . $3 . "\n";


#domain/path/.*/path/filename
} elsif (($X[1] =~ /****tube/) && (m/^http:\/\/(.*?)(\.[^\.\-]*?[^\/]*\/[^\/]*)\/(.*)\/([^\/]*)\/([^\/\?\&]*)\.([^\/\?\&]{3,4})(\?.*?)$/)) {
@y = ($1,$2,$4,$5,$6);
$y[0] =~ s/(([a-zA-A]+[0-9]+(-[a-zA-Z])?$)|([^\.]*cdn[^\.]*)|([^\.]*cache[^\.]*))/cdn/;
print $x . "http://" . $y[0] . $y[1] . "/" . $y[2] . "/" . $y[3] . "." . $y[4] . "\n";


#like porn hub variables url and center part of the path, filename etention 3 or 4 with or without ? at the end
} elsif (($X[1] =~ /tube8|pornhub|xvideos/) && (m/^http:\/\/(([A-Za-z]+[0-9-.]+)*?(\.[a-z]*)?)\.([a-z]*[0-9]?\.[^\/]{3}\/[a-z]*)(.*?)((\/[a-z]*)?(\/[^\/]*){4}\.[^\/\?]{3,4})(\?.*)?$/)) {
print $x . "http://cdn." . $4 . $6 . "\n";


#for yimg.com video
} elsif (m/^http:\/\/(.*yimg.com)\/\/(.*)\/([^\/\?\&]*\/[^\/\?\&]*\.[^\/\?\&]{3,4})(\?.*)?$/) {
print $x . "http://cdn.yimg.com/" . $3 . "\n";


#for yimg.com doubled
} elsif (m/^http:\/\/(.*?)\.yimg\.com\/(.*?)\.yimg\.com\/(.*?)\?(.*)/) {
print $x . "http://cdn.yimg.com/" . $3 . "\n";


#for yimg.com with &sig=
} elsif (m/^http:\/\/([^\.]*)\.yimg\.com\/(.*)/) {
@y = ($1,$2);
$y[0] =~ s/[a-z]+([0-9]+)?/cdn/;
$y[1] =~ s/&sig=.*//;
print $x . "http://" . $y[0] . ".yimg.com/" . $y[1] . "\n";


#youjizz. We use only domain and filename
} elsif (($X[1] =~ /media[0-9]{1,5}\.youjizz/) && (m/^http:\/\/(.*?)(\.[^\.\-]*?\.[^\/]*)\/(.*)\/([^\/\?\&]*)\.([^\/\?\&]{3,4})(\?.*?)$/)) {
@y = ($1,$2,$4,$5);
$y[0] =~ s/(([a-zA-A]+[0-9]+(-[a-zA-Z])?$)|([^\.]*cdn[^\.]*)|([^\.]*cache[^\.]*))/cdn/;
print $x . "http://" . $y[0] . $y[1] . "/" . $y[2] . "." . $y[3] . "\n";


#general purpose for cdn servers. add above your specific servers.
} elsif (m/^http:\/\/([0-9.]*?)\/\/(.*?)\.(.*)\?(.*?)/) {
print $x . "http://squid-cdn-url/" . $2 . "." . $3 . "\n";


# spicific extention
# } elsif (m/^http:\/\/(.*?)\.(jp(e?g|e|2)|gif|png|tiff?|bmp|ico|flv|wmv|3gp|mp(4|3)|exe|msi|zip|on2|mar|swf).*?/) {
# @y = ($1,$2);
# $y[0] =~ s/((cache|cdn)[-\d]*)|([a-zA-A]+-?[0-9]+(-[a-zA-Z]*)?)/cdn/;
# print $x . "http://" . $y[0] . "." . $y[1] . "\n";


#generic http://variable.domain.com/path/filename."ex", "ext" or "exte"
#[http://cdn1-28.projectplaylist.com](http://cdn1-28.projectplaylist.com)
#[http://s1sdlod041.bcst.cdn.s1s.yimg.com](http://s1sdlod041.bcst.cdn.s1s.yimg.com)
} elsif (m/^http:\/\/(.*?)(\.[^\.\-]*?\..*?)\/([^\?\&\=]*)\.([\w\d]{2,4})\??.*$/) {
@y = ($1,$2,$3,$4);
$y[0] =~ s/([a-z][0-9][a-z]dlod[\d]{3})|((cache|cdn)[-\d]*)|([a-zA-A]+-?[0-9]+(-[a-zA-Z]*)?)/cdn/;
print $x . "storeurl://" . $y[0] . $y[1] . "/" . $y[2] . "." . $y[3] . "\n";


# all that ends with ;
} elsif (m/^http:\/\/(.*?)\/(.*?)\;(.*)/) {
print $x . "http://" . $1 . "/" . $2 . "\n";


} else {
print $x . $X[1] . "\n";
}
}




sub GetID
{
$id = "";
use File::ReadBackwards;
my $lim = 200 ;
my $ref_log = File::ReadBackwards->new('/var/log/squid/yt.log');
while (defined($line = $ref_log->readline))
{
if ($line =~ m/.*youtube.*\/watch\?.*v=([a-zA-Z0-9\-\_]*).*\s.*id=$IDS[0].*/){
$id = $1;
last;
}
if ($line =~ m/.*youtube.*\/.*cpn=$CPN[0].*[&](video_id|docid|v)=([a-zA-Z0-9\-\_]*).*/){
$id = $2;
last;
}
if ($line =~ m/.*youtube.*\/.*[&?](video_id|docid|v)=([a-zA-Z0-9\-\_]*).*cpn=$CPN[0].*/){
$id = $2;
last;
}
last if --$lim <= 0;
}
if ($id eq ""){
$id = $IDS[0];
}
$ref_log->close();
return $id;
}

```


[COLOR=#333333][FONT=Trebuchet MS]
and this is my problem 
cache became read only after a couple hours,chown an chmod didn't work at that times
[/FONT][/COLOR][FONT=trebuchet ms]after I unmount both partitions then I mounted again it back to normal, squid work again[/FONT]
[FONT=trebuchet ms]what's wrong with my ubuntu or squid, please help me...

sorry for my bad english...[/FONT]

---

