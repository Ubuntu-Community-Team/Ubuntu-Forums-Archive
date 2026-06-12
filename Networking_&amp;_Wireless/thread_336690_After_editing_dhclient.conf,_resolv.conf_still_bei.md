---
title: "After editing dhclient.conf, resolv.conf still being overwritten, disabling dsl.."
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by batholith on 2007-01-11
First my apologies for being the kabillionth thread related to this "problem"...I've searched through the forums for hours, but haven't found the answer to my select problem.  

Here's my situation, I recently hooked up a dsl modem and was having problems with getting the connection established at boot.  I went throught the general procedure [COLOR="DarkOrange"][here]("http://ubuntuforums.org/showpost.php?p=1925014&postcount=5")[/COLOR] (except for using my own dns name, not OpenDSLs), to modifiy my dhclient.conf file (it was overwriting resolv.conf with bad dns info). Here it is:

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
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 216.165.129.157, 216.170.153.146;
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
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

However, my resolv.conf file is still be inserted with bad name servers.  

One thing I've noticed is that my "search domain" under network preferences keeps getting changed...I don't know how to permanently set that in the dhclient.conf file...any suggestions?

The only other "wierd" thing that happens is within my /etc/network/interfaces file.  See below:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# added by pppoeconf


iface eth0 inet dhcp

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

auto eth0

```

The last line "auto eth0" keeps getting re-written to the bottom of the file.  I move it directly above "iface eth- inet dhcp", but ubuntu keeps moving it back...Does the order matter??  Anything else look fishy?  

Thanks in advance

---

### Post by batholith on 2007-01-12
OK so I've played around a bit more and figured out the search domain thing...

I activated the "supercede domain-name" line in the dhclient.conf and it added the appropriate inserted search domain...

I've also found that the only way I can browse on the web after a reboot is if I perform the following commands:

$sudo poff 
$sudo /etc/init.d/networking restart

Selecting the graphical System->Preferences->Networking , then deactivating->activating only allows web-browsing for about 10 seconds....???

Any ideas?

---

