---
title: "Ubuntu Proxy Server"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by dwilliams07 on 2010-12-04
Hi, I'm considering purchasing a mac mini server for the home and install Ubuntu server. Our current setup is a few windows xp and mac os x leopard machines. I would like the mac mini to handle network authentication and file sharing. I'm also interested in using the mac mini as a proxy server to monitor the sites my kids visit. I've been searching for solutions and it appears that a program called Squid is highly recommended. Unfortunately it doesn't appear to be the easiest to configure (it doesn't appear to have a GUI). I just want something simple that I can quickly pull reports on the sites my kids visit, and also quickly enter the sites that I don't want them to be able to visit. After doing more research it appears that you can install a GUI on top of squid. Can somebody tell me if I'm going in the right direction or making things hard on myself? Also, if you think a different version of Linux running on a pc could accomplish the same results please let me know. Thanks.

P.S. I've only been using Ubuntu off and on for a few years.

---

### Post by The Real Dave on 2010-12-04
Squid is fantasitic, I use it on my own server as a cache.

The default config is massive (>5000 lines) but the majority of that comprises of comments, explaining what each option does. If you know how to edit a document using nano or vim at the command line, then you can configure Squid.

I've uploaded my config, which is fairly basic. Adding on exclusions to prevent access to certain sites is simple. Also, this config allows/blocks certain ports, adding an extra layer of security.

You'll want to change things such as the cache and log location and also the acl localnet to suit your own network. At the very bottom of the config, I've it set not to cache ubuntu updates, seeing as I use another proxy server to cache all updates.

I'd also advise installing the latest version of Squid3 rather than using the older versions from the repos.

To block a site, simply add

```
acl blocksites url_regex "/etc/squid3/squid-block.acl"
http_access deny blocksites
```

to your config, then create a file called squid-block.acl in /etc/squid3/ with the urls you wish to block, or just words. Put each variable on a seperate line.

For example, the config

```
.foo.com
stuff
```

should block any site at foo.com or any domain with "stuff" in it's name.

If your're unfamilar with editing files in command line, have a read of [Nano for beginners.]("https://help.ubuntu.com/community/Nano")

Best of luck mate. :)

My config.
```
#START

#General
visible_hostname an-lar
hosts_file /etc/hosts
high_memory_warning 100 MB
http_port 3128

#Logs
access_log /home/dave/.Reports/squid/access.log 
cache_log /home/dave/.Reports/squid/cache.log
cache_store_log /home/dave/.Reports/squid/store.log

#Think about adding stuff from refresh_pattern

#Cache Options
cache_mgr davidj086@xxxxxx.xx
cache_dir ufs /home/squid 15000 16 256
#cache_dir ufs /home/dave/temp 100 16 256

#DNS 
dns_nameservers 8.8.8.8 8.8.4.4	#Google Nameservers

#Jesred Redirecting (Apt-Cacher-NG)
#redirect_program /usr/lib/squid/jesred
#redirect_children 5

#ACL
#acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 192.168.15.0/24
#	#ACL Ports
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
acl Safe_ports port 11371       # keyserver
acl purge method PURGE
acl CONNECT method CONNECT
#	#Access based on ACL
# 	#	Only allow cachemgr access from localhost
http_access allow manager localhost
http_access deny manager
# 	#	Only allow purge requests from localhost
http_access allow purge localhost
http_access deny purge
# 	#	Deny requests to unknown ports
http_access deny !Safe_ports
# 	#	Deny CONNECT to other than SSL ports
http_access deny CONNECT !SSL_ports
#	#Give access to previously defined networks
http_access allow localnet
http_access allow localhost
#	#	Allow ICP queries from local networks only
icp_access allow localnet
icp_access deny all
#ACL for Squid not to cache
acl ubuntu_updates dstdomain .ubuntu.com
always_direct allow ubuntu_updates
#acl ubuntu_keyserver dstdomain keyserver.ubuntu.com
#always_direct allow ubuntu_keyserver

#END

```

---

### Post by dwilliams07 on 2010-12-05
Thank you very much for your help.

---

### Post by The Real Dave on 2010-12-06
No worries mate. If you've got any questions, I'll do my best to answer them.

---

### Post by dwilliams07 on 2010-12-17
The Real Dave,

I should have asked another question before posting the one about Squid.  Do you have any experience or advice you can give me for setting up Ubuntu server as a PDC?  I've been reading bits and pieces of information suggesting SAMBA.  To be honest, I'm still in the newbie phase and was glad to hear that I could install GNOME as a GUI.  I'm always pressed for time and I need a GUI to help get up and running quickly.  At any rate, I need to first setup a PDC for 3 XP laptops and 1 Mac OS X laptop.  From there, I would like to install Squid to handle proxy functions.  

Any advice you can give or point me to is greatly appreciated.

---

### Post by The Real Dave on 2010-12-17
I'm not familiar with Samba PDC, from a quick Google, I gather it's some sort of domain controller for Windows clients? If it is, then no, I don't have any real experience in that.

You can indeed install Gnome if you'd rather use a GUI, but being honest, most of the things you'll do will be editing text files, which can all be done through CLI and SSH. 

However, I did [write a Howto]("http://linuxexpresso.wordpress.com/2010/10/17/howto-ubuntu-vnc-encoding-server/") on how to setup a lightweight Gnome desktop on Ubuntu server, and share it over VNC, allowing you to login remotely. It might just do perfectly for you, especially if you don't want to have a screen and keyboard connected to your machine, just power and network.

---

### Post by dwilliams07 on 2010-12-17
Thanks again for your help.

---

### Post by The Real Dave on 2010-12-18
Mo worries mate.

---

