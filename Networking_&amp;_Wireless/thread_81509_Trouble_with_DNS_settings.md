---
title: "Trouble with DNS settings"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by tehwa on 2005-10-24
I have recently setup a new ADSL connection. After succesfully getting the connection working through the modem/router web config page, I had some issues with DNS that are giving me a headache.

Basically, /etc/resolv.conf lists my gateway IP by default, and does not seem to work for me. If I manually add my DNS server for my ISP [203.0.178.191] my connection run work smoothly, until resolv.conf is overwritten.

I have tried modifying /etc/dhcp3/dhclient.conf to write my proper DNS server into resolv.conf, but everything I try seems to put 127.0.0.1 before my real DNS server, which keeps my connection from working unless I remove it every 8 minutes or so.

I basically need the dhcp3 script to write the working resolv.conf, rather than the b0rked resolv.conf it is writing:

Working example of resolv.conf:
```

nameserver 203.0.178.191
nameserver 192.168.0.1
```
B0rked example, that is written to resolv.conf automagically:
```

nameserver 127.0.0.1
nameserver 203.0.178.191
nameserver 192.168.0.1
```
Here's my dhclient.conf
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "203.0.178.191";
prepend domain-name-servers 203.0.178.191;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 203.0.178.191;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

(http will work when 127.0.0.1 is written to resolv.conf, but apt-get update lists all server IP's as 1.0.0.0???)

TIA

---

### Post by stream303 on 2006-01-16
You got real close with your /etc/dhcp3/dhclient.conf file.  Check your "supersede" line:

supersede domain-name-servers 203.0.178.191;

What got me early on was using server instead of servers
and forgetting the semicolon at the end.  No quotes needed around the ip address.

Do you still get 127.0.0.1  as the first line now?

---

