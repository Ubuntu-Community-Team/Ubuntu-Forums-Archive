---
title: "issue resolving IP address in OS"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by trent1980 on 2008-04-17
I'm having trouble trying to resolve addresses in applications like pidgin ...

trent@trent-laptop:~$ ping jabber.ssi.local
ping: unknown host jabber.ssi.local

trent@trent-laptop:~$ nslookup
> jabber.ssi.local
Server:		192.168.1.240
Address:	192.168.1.240#53

Name:	jabber.ssi.local
Address: 192.168.1.250


I have a DNS server and the DNS server is holding the record for the jabber server ... but Pidgin replies with unable to contact the server. I believe its more of a general resolution issue. Do I have to do anything in order to allow DNS lookups for the applications?

Thanks in advance,
Trent

---

### Post by superprash2003 on 2008-04-17
have you added your DNS servers in the dhclient.conf file?

---

### Post by trent1980 on 2008-04-18
Do i need to? It's DHCP ... It looks like it is requesting DNS servers. I can access the internet just fine and resolve webpages ... just not internal servers.

Here is my dhclient.conf:

# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
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
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

