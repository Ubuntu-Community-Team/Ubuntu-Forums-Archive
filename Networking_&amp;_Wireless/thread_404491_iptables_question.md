---
title: "iptables question"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by ubiworld on 2007-04-08
hi i have a problem here...

i have two PC (A and B), one (B) is running a virtual machine (on VMWARE). i stablished an IPSec tunnel between the virtual machine and the PC A. So i need to know how to do in case that, if i do a query through firefox, for example on the virtual machine, the request should be perform by PC A and send the result  to the virtual machine and see the webpage on the VM. Any idea of how to do this? I was trying to use iptables but it hasn't worked yet. I've successfully made that the request for DNS arrives to PC A. but thats all, PC A doesn't perform the request.

Any help???
thanks

---

### Post by Roland of Gilead on 2007-04-08
From your post, it sounds like what you're looking for is an HTTP proxy.

Example:

Machine B is not directly connected to the internet, but Machine A is.  You want to be able to open Firefox on B and browse to a website as though it was connected, using Machine A as a "gateway."  In this scenario, A functions as a proxy for B.

You need an HTTP proxy server running on machine A.  SQUID is an excellent choice, and is included in many Linux distros.  This proxy server listens for requests from other machines on a designated port (TCP 3128 is the Squid default) and returns the destination server responses to the requesting host.

Once you have the proxy server installed and running, you need to configure the browser on machine B to use the proxy.  You'll find the settings in the Connection Preferences of Firefox...you supply the hostname and port of the proxy, and you're all set.  Example: *machinea:3128*

For non-browser utilities to use the proxy (such as wget, apt-get, etc), you'll need to set two global environment variables:

EXPORT http_proxy=http://machinea:3128
EXPORT ftp_proxy=http://machinea:3128



EDIT:
Duh...you'll also need to alter iptables on Machine A to allow inbound traffic on whichever TCP port you decide to have the proxy server listen on.  The nice thing about iptables is that you can limit this opening to specific hosts or subnets, restricting which machines can utilize the proxy service.

---

### Post by ubiworld on 2007-04-08
OK man! It worked perfectly...

But I have a small problem with Squid now. It denies access to the Virtual Machine to any page.

It says Access Denied to any page we enter in Firefox.

We looked at the squid.conf file like 11 times now and it is virtually allowing anything.

But I don't know what is happening that it doesn't allow the network access to the Virtual Machine.

Please, tell me exactly what I need to add in  the squid.conf file.

Thanks

---

### Post by Roland of Gilead on 2007-04-08
Hmmm...I thought Squid allowed access to all clients for all resources in the default configuration.  Access control is provided using ACL entries in squid.conf...look for lines containing "http_access"

Can you attach your configuration file to this thread so I can take a look?

---

### Post by ubiworld on 2007-04-08
mmm this file is very large.. it has so many comment lines. this is the code without the comments (I hope not to have left any uncomment line)

```


http_port 3128

acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY


hosts_file /etc/hosts

#auth_param digest program <uncomment and complete this line>
#auth_param digest children 5
#auth_param digest realm Squid proxy-caching web server
#auth_param digest nonce_garbage_interval 5 minutes
#auth_param digest nonce_max_duration 30 minutes
#auth_param digest nonce_max_count 50
#auth_param ntlm program <uncomment and complete this line to activate>
#auth_param ntlm children 5
#auth_param ntlm max_challenge_reuses 0
#auth_param ntlm max_challenge_lifetime 2 minutes
#auth_param basic program <uncomment and complete this line>
#auth_param basic children 5
#auth_param basic realm Squid proxy-caching web server
#auth_param basic credentialsttl 2 hours

refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320

acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443 563	# https, snews
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

http_access allow manager localhost all
#http_access deny manager
# Deny requests to unknown ports
#http_access deny !Safe_ports
http_access allow !Safe_ports
# Deny CONNECT to other than SSL ports
#http_access deny CONNECT !SSL_ports
http_access allow CONNECT !SSL_ports
http_reply_access allow all

icp_access allow all

coredump_dir /var/spool/squid


visible_hostname puma



#acl GoodSites dstdomain "/usr/local/etc/allowed-sites.squid"



#acl nuestrared src 159.90.21.0/255.255.255.240
#acl localhost src 127.0.0.1/255.255.255.255
#http_access allow localhost
#http_access allow nuestrared GoodSites

#httpd_accel_host puma
#httpd_accel_port 80
#httpd_accel_with_proxy on
#httpd_accel_uses_host_header off

#acl home_network src 159.90.21.164
#http_access allow home_network
#http_access allow localhost


```

thanks for your time man ^^

---

