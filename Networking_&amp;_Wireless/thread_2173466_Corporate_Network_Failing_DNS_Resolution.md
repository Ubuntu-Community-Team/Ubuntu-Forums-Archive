---
title: "Corporate Network: Failing DNS Resolution"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by Illydth on 2013-09-09
I hope this isn't a rehash of 20 other posts.

I'm using Kubuntu 13.04 as my main System at work.

I'm seeing serious DNS Resolution issues:  Static DNS records will change at work and I'm not getting them.  More confusing is that my /etc/resolv.conf is showing 127.0.0.1 as my resolver (and ONLY that address) so I assume i'm using some kind of DNS Cache on the system.

Any changes I make to the /etc/resolv.conf file get overwritten at reboot by something called "resolvconf" who's man mage gives me no information about how to set an additional resolver permanently.

I seem to be using NetworkMangager (which I tend to turn off on all of my installations of RHEL / Fedora / Cent) which I suspect to be half the problem.  I have nothing against NetworkManager (it's working well enough on my PC here) but it tends to obvuscate every network setting on the box.

NSCD is installed and something called dnsmasq is running.  I can shutdown NSCD and port 53 stays open, so I have to assume that isn't what's resolving network addresses.  That leads me to dnsmasq but I have NO idea what the hell is running that since it's not a service in /etc/init.d.

I either need to be able to put resolvers in prior to 127.0.0.1 (my corporate resolvers), or figure out how to force update the DNS Cache regularly (as in, whenever the heck I add a record to DNS), so I don't have to keep hopping to other servers to get to ones I've just built.

Help?  I'm an RHEL Guy who's delt in Ubuntu for several years, but Debian/Ubuntu's Networking is still a complete black box to me (no /etc/sysconfig, /etc/sysconfig/network and /etc/sysconfig/network-scripts).

--Illydth

---

### Post by chili555 on 2013-09-09
The quick, easy and not too dirty way is to click the Network Manager icon, edit connections for either wired or wireless, whichever you use, and change the IPv4 setting from Automatic (DHCP) to Automatic (DHCP) addresses only and then specify your own DNS nameservers. Please see: [http://cache.gawkerassets.com/assets/images/lifehacker/2009/12/ubuntu_dns.jpg](http://cache.gawkerassets.com/assets/images/lifehacker/2009/12/ubuntu_dns.jpg)  The ones in the illustration are pretty good, actually.

---

### Post by jdthood2 on 2013-09-10
For background information please read this: [https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by Illydth on 2013-09-13
Thanks Gents (or ladies as the case may be!) I'll take a look at both of those and get this worked out! :)

---

