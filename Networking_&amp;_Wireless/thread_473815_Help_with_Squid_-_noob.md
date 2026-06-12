---
title: "Help with Squid - noob"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by Sig_ZA on 2007-06-14
I have installed squid and the only change to the config file was to include a 'unique_hostname'.
When restarting squid '$ sudo /etc/init.d/squid restartf' I get an OK with no warnings.

The linux machine and the windows machines obtain their IP addresses from a router.
The proxy setting in the web browser is set to 192.168.0.2:3128 (the linux machine).

linux machine:
# ifconfig gives eth0 as ' inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0'.
And pings 192.168.0.2 (itself) and 192.168.0.1 (router) ok.

But when using the web browser on a windows machine, it times out 'could not connect to proxy server.'

What am I doing wrong. :confused:

---

### Post by alan34 on 2007-06-14
Are the window machines set up to look for the proxy server on the linux machine?

In Firefox  

Edit - Preferences - Advanced - Network - Settings

Then

Manual Proxy configuration radio button

In HTTP should be for yours

192.168.0.2      (IP of your linux machine)
Port 80

Use for all settings.

Quite a task you have set yourself good luck;)

Loads of settings in squid, look for something like acl_allow on your ports make sure
port 80 and port 443 is allowed, not at work so cannot look at our server to give you
a config file.

---

### Post by Sig_ZA on 2007-06-15
[QUOTE=alan34]Are the window machines set up to look for the proxy server on the linux machine?[/QUOTE]
Yes.
[QUOTE=Sig_ZA]The proxy setting in the web browser is set to 192.168.0.2:3128 (the linux machine).[/QUOTE]
But set to port 3128, not 80 as I understand squid uses this port by default.

I'm not sure how the acl_allow setting works. I tried setting "http_access allow 192.168.0.2/192.168.0.255' but get an error when restarting squid.

> * Restarting Squid HTTP proxy squid                                            2007/06/15 06:08:02| ACL name '192.168.0.3' not defined!
FATAL: Bungled squid.conf line 2592: http_access allow 192.168.0.2/192.168.0.255
Squid Cache (Version 2.6.STABLE5): Terminated abnormally.


---

### Post by airtonix on 2007-06-15
you might also want to make sure that your firewall is not blocking the traffic.

---

### Post by alan34 on 2007-06-15
Hi, these are files from my Debian server at work. We use a fixed IP addresses.
squid.txt is the commands to install and set up directory permissions - you will
have to use sudo in front of them.
squid.conf.txt is the configuration file - I know this works done it myself;)

---

### Post by alan34 on 2007-06-15
help where the attachment gone

---

### Post by alan34 on 2007-06-15
hope it here now

---

### Post by Sig_ZA on 2007-06-16
My problem seems to be setting up squid to allow access from IPs in my network.

I've narrowed the squid.config commands down to **acl** and **http_access**.

Can anyone please help me with the config settings for normal http access. The server is on 192.168.0.2 (also needs access), the router 192.168.0.1 and the rest of the network (2 machines) are from 192.168.0.3 and above.

I have visted [http://www.squid-cache.org/]("http://www.squid-cache.org/"), but it's all gobble-dee-goo for me. :p

---

### Post by alan34 on 2007-06-16
Should have these in your squid.conf

#
#Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563
acl Safe_ports port 80  	# http
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
#
#  This line enables https connections 
#  Only in FAQs on squid website
#
acl SSL method CONNECT
#
#
#

and 


#
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
#      
#
acl allowed_hosts1 src  192.168.0.3/255.255.255.255
http_access allow allowed_hosts1
icp_access allow allowed_hosts1
#
#       
#
acl allowed_hosts2 src  192.168.0.4/255.255.255.255
http_access allow allowed_hosts2
icp_access allow allowed_hosts2
#

etc for as many machines as you like.

Did you look at the files I posted? I would recommend using fixed IP addresses
and also are you running a nameserver program such as Bind on your server
so it knows which machine is which. When I set squid up at work took about 3 days
so be prepared for a long haul.

You know you can run Apache as a web server for your other machines not saying
it is any easier but.............................

Good Luck

---

### Post by Sig_ZA on 2007-06-16
@alan34

Hi, yes I did look at your config file. Thanks.
I started with squid's default config file and compared it to yours using Meld.
They are basically identical but for the acl and http_access sections, obviously.

In the mean time I added the lines.
> acl mynetwork src 192.168.0.1-192.168.0.10
http_access allow localhost

And I got nothing. I then changed them to your suggested lines in the above post and still nothing.

I really don't understand what the problem is. There is absolutely nothing complicated about my requirements. Four PC's connecting to a proxy server on one of the PC's for http only.

This took me 10 minutes with my previous distro that came with a nice wizard which basically asked two questions if I can remember.

I'm starting to get a bit frustrated here. From what I've been reading the default conf should work out the box with a few small changes.

---

### Post by Sig_ZA on 2007-06-16
At freaking last! :D

Seems as if I confused  **visible_hostname** with **unique_hostname**.
Found this out when I stumbled across a log file** /var/log/squid/cache.log** and found that the server halted during a restart at this point.

For the record (and anyone else going down this road), these are the only changes that I needed to make to the default squid.conf file to get basic http caching.

> visible_hostname = linuxproxyserver
http_access deny to_localhost (this was not required, but may be needed once I get apache going).
acl mynetwork src 192.168.0.1-192.168.0.10
http_access allow mynetwork


As it turns out, all you need is on ubuntu's [help]("https://help.ubuntu.com/7.04/server/C/squid.html") pages. But only now makes sense to me.

Thanks alan34 for your help.

---

