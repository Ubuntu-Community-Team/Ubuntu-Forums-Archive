---
title: "Gutsy 7.10 on HP laptop not accessing internal DNS"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by bunadm on 2008-01-13
Hi all!

1st post.

I have a small network, servers are Suse 10.3, clients are ubuntu 7.10, 7.04 & windows XP.

Running DNS(for internal resolution) on SUSe 10.3, and it works for for all my clients except my ubuntu laptop.

I have manually entered the DNS IP in the network configuration, restarted networking, rebooted, and nothing...

Router(172.18.10.1) DNS relay from ISP
SUse 10.3 (172.18.10.10) running BIND, configured with webmin. forwards to the ISP DNS.

If I use NSlookup from the ubuntu laptop,  see below for xterm results:

fuentej@CSRHPLT01:~$ nslookup
> server
Default server: 172.18.10.1
Address: 172.18.10.1#53

> csrdev01
Server:         172.18.10.1
Address:        172.18.10.1#53

** server can't find csrdev01: NXDOMAIN

> server 172.18.10.10
Default server: 172.18.10.10
Address: 172.18.10.10#53

> csrdev01
Server:         172.18.10.10
Address:        172.18.10.10#53

** server can't find csrdev01: NXDOMAIN

> csrdev01.csr.org
Server:         172.18.10.10
Address:        172.18.10.10#53

Name:   csrdev01.csr.org
Address: 172.18.10.200
> 

IE... it only works if I point nslookup to the DNS server, and use the FQDN. 
(my other PCs I just manually input the DNS server in the network config and it works great!)

If I edit /etc/resolv.conf and save, exit, restart networking... and the entries i just put in resolv.conf are gone... Don't know why???

I assume something is over writing resolv.conf, but I do not know what...

And like I said, it's only a problem on the ubuntu laptop 7.10

Please help :)

---

### Post by sqrt2 on 2008-01-13
Add the line
[indent]search csr.org[/indent]
to your /etc/resolv.conf.

---

### Post by bunadm on 2008-01-13
followup...

dhclient.conf


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

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
supersede domain-name "csr.org";
prepend domain-name-servers 172.18.10.10;
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
=========================================================

When I restart networking I get the following error_

fuentej@CSRHPLT01:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                       
There is already a pid file /var/run/dhclient.eth0.pid with pid 8364
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

[B][COLOR="Red"]/etc/dhcp3/dhclient.conf line 18: 172.18.10.10 (262): expecting IP address or hostname
prepend domain-name-servers "172.18.10.10"
                            ^
/etc/dhcp3/dhclient.conf line 18: expecting a statement.
prepend domain-name-servers "172.18.10.10";
                                          ^
/etc/dhcp3/dhclient.conf line 23: semicolon expected.
timeout [/COLOR][/B]
^
Listening on LPF/eth0/00:14:38:15:6d:c3
Sending on   LPF/eth0/00:14:38:15:6d:c3
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 172.18.10.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

/etc/dhcp3/dhclient.conf line 18: 172.18.10.10 (262): expecting IP address or hostname
prepend domain-name-servers "172.18.10.10"
                            ^
/etc/dhcp3/dhclient.conf line 18: expecting a statement.
prepend domain-name-servers "172.18.10.10";
                                          ^
/etc/dhcp3/dhclient.conf line 23: semicolon expected.
timeout 
^
Listening on LPF/eth0/00:14:38:15:6d:c3
Sending on   LPF/eth0/00:14:38:15:6d:c3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 172.18.10.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.18.10.1
bound to 172.18.10.100 -- renewal in 42483 seconds.

---

### Post by bunadm on 2008-01-13
sqrt2 - 

It is just overwritten when I restart networking or the dhcp client, or reboot...

I think I may have a syntax problem with my edit of the dhcp client config...

Please see my reply above...

Thanks tho!

---

### Post by sqrt2 on 2008-01-13
Since you run an own DNS server, it seems quite likely that you also run a DHCP server that pushes it to the clients. You shouldn't have to mess with your dhclient.conf. (The quotes around the IP address cause the error btw.)

As I said, to tell the resolver to look for names in the domain csr.org, add the line I posted above to /etc/resolv.conf. If you run dhcp3 as a DHCP server, you can have this done automatically by adding
[indent]option domain-name "csr.org";[/indent]
to dhcpd.conf.

---

### Post by bunadm on 2008-01-13
My DHCP is running off the router, and it does not have an option to push out my DNS...

It will only relay the ISP DNS... It's a kyocera KR1 and I am kinda stuck with it because my WAN is an EVDO card.

And as I said, any edits to the resolve.conf get overwritten when networking or the dhcp client are restarted.

I will try the option you mentioned tho...

thx

---

### Post by sqrt2 on 2008-01-13
Your getting your IP address via DHCP but have to configure your DNS server manually? What you're looking for then are the options
[indent]prepend domain-name-servers 172.18.10.10;
prepend domain-name "csr.org";[/indent]
in your dhclient.conf. Note that there are no quotes around the IP address.

---

### Post by bunadm on 2008-01-13
Ok, cool its working now...

one odd thing is that now when I ping the FQDN it replies a little odd.

I dont think it will effect anything much, but if its fixable, I'd rather fix it.

fuentej@CSRHPLT01:~$ **ping csrdev01.csr.org**
PING** csrdev01.csr.org** (172.18.10.200) 56(84) bytes of data.
64 bytes from **csrdev01.local** (172.18.10.200): icmp_seq=1 ttl=64 time=3.18 ms
64 bytes from csrdev01.local (172.18.10.200): icmp_seq=2 ttl=64 time=0.377 ms
64 bytes from csrdev01.local (172.18.10.200): icmp_seq=3 ttl=64 time=0.366 ms
64 bytes from csrdev01.local (172.18.10.200): icmp_seq=4 ttl=64 time=0.370 ms
64 bytes from csrdev01.local (172.18.10.200): icmp_seq=5 ttl=64 time=0.357 ms

--- csrdev01.csr.org ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 0.357/0.930/3.181/1.125 ms

fuentej@CSRHPLT01:~$ ping **csrdev01**
PING csrdev01.csr.org (172.18.10.200) 56(84) bytes of data.
64 bytes from** csrdev01.local** (172.18.10.200): icmp_seq=1 ttl=64 time=0.362 ms
64 bytes from csrdev01.local (172.18.10.200): icmp_seq=2 ttl=64 time=0.324 ms
64 bytes from csrdev01.local (172.18.10.200): icmp_seq=3 ttl=64 time=0.356 ms

--- csrdev01.csr.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.324/0.347/0.362/0.022 ms

---

### Post by sqrt2 on 2008-01-13
Normally, names in the "local" zone are resolved via Multicast DNS, which csrdev01 probably provides. Try adding
[indent]mdns off[/indent]
to /etc/host.conf.

---

### Post by bunadm on 2008-01-13
on which box?

csrdev01 or my ubuntu laptop?  or all?

thx

---

### Post by sqrt2 on 2008-01-13
On your Ubuntu box. It tells the resolver not to use Multicast DNS.

---

### Post by bunadm on 2008-01-14
Kool, thanks!

---

