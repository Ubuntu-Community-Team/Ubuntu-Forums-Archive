---
title: "Business Network - IP Masquerade, dnsmasq, ipmasq, ip_forward, Iptables, Proxy etc"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by fromvega on 2006-12-11
Hello,

First of all I would like to thank you, the community, for all the help available out there in the forum and in other sites. 

My question is about Linux Networking as you may already imagine. The problem is that I'm not used with some aspects of Linux Networking, although I have used some applications that I will mention in this thread I do not have experienced them all together.

Basically I want to setup a network with a Linux machine acting as a router, DHCP server, Transparent Proxy, NAT and firewall (basically it's what I get with my actual configuration using an ADSL/Router modem and WindowXP - minus the proxy).

My network configuration is the following:

-->[ ADSL Modem ]--->[ Linux Box ]--->[ HUB  Switch ]==>[ Clients ]

I have read much about those services and how to configure them but I still have some doubts. I realized that there are many ways to achieve the intent and some posts/articles say that their configurations are only suitable for home networks.

First, I would like to know the difference between a home and a business configuration. I want to do the business way.

Second, I would like to know how should I configure the modem in my actual layout. The only one that worked for me is to leave it as IP router (Bridge didn't work).

Third, I have read much about IP Masquerade, dnsmasq, ipmasq, ip_forward, Iptables. How do they interact with each other? Some articles say to use dnsmasq, others BIND. Which should I use?

Fourth, some say to use ip masquerade instead of NAT. What's the difference? I need to have a transparent proxy where I can block access to the WAN only allowing specific services to certain machines. Should I use NAT with SQUID and what else?

Fifth, SQUID is just a HTTP proxy, what should I use for blocking messengers and SMTP, POP etc? How can I limit the bandwidth for the client machines?

Sixth, I would like to DHCP. Some say that Ubuntu is shipped with a DHCP server accessed by dhcpd, others say to install dhcp3-server. Which is the difference?

Thank you for your patiente reading until here. I would be thankfully if you help me at least in one of these.

---

