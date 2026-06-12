---
title: "trouble in configuring dhcp server"
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by aznavur on 2005-11-19
Hi, everyone. I have Siemens Gigaset SE105 dsl/cable wireless router connected to my dual boot desktop(XP - Kubuntu 5.04). Also I have Speedtouch 330 ADSL modem(silver colored) connected to USB port. I want internet to be available to my laptop(XP) via wireless.

As far as I know, I have to configure Kubuntu as dhcp server. I have downloaded necessary package dhcp3-server. I configured /etc/dhcp3/dhcpd.conf as follows:

option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
subnet 192.168.0.1 netmask 255.255.255.0 {
	range 192.168.0.10 192.168.0.254;
}

But when I tried to do "dhcpd3 start" it gives the following message:

Internet Systems Consortium DHCP Server V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
/etc/dhcp3/dhcpd.conf line 36: subnet 192.168.0.1 netmask 255.255.255.0: bad subnet number/mask combination.
subnet 192.168.0.1 netmask 255.255.255.0
                                                                    ^
Configuration file errors encountered -- exiting

(the ^ points out zero of 255.255.255.0) That sounds weird since netmask is 255.255.255.0 under XP and it works fine.  Does anyone have an idea? Thanks for your help.

---

