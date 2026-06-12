---
title: "Severe degradation of network connectivity -- DNS resolution"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by jsfritz on 2006-10-25
Hello.

I have just installed 6.10 Edgy Eft.  Everything works fine save for internet connectivity, which is sporadic.

I did some research and found that Ubuntu searches for ipv6 resolution first, then ipv4, and that this will produce the symptoms I'm experiencing.

I've followed the instructions at [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) -- to no avail.  "ip -a | grep ivp6" returns nothing, however, the same symptoms occur -- seconds, even minutes before a page will load, but once it starts loading, it loads quickly.

I've installed dnsmasq and set the appropriate files to look for localhost's DNS server first, in an attempt to speed up DNS caching and lookup.  However, this seems to have had no effect at all save for testing DNS lookup time using "dig".  Issues started even before I isntalled dnsmasq.

Symptoms occur with any program that uses internet connectivity.

Any help would be greatly appreciated.

---

### Post by towsonu2003 on 2006-10-26
what if it's bc of your dns servers? have a look at [http://www.opendns.com/](http://www.opendns.com/)

also, try disabling ipv6 in firefox as well: go to about:config and set "network.dns.disableIPv6" to true

---

### Post by jsfritz on 2006-10-26
As I've said, the issues started before I installed dnsmasq, so dnsmasq isn't causing any problems.   The symptoms before and after dnsmasq installation are the same.

Firefox is set for ipv6 to be disabled.  As I've said, the issues happen with all internet connectivity programs.

---

### Post by towsonu2003 on 2006-10-26
> **towsonu2003 said:**
> what if it's bc of your dns servers? have a look at [http://www.opendns.com/](http://www.opendns.com/)

> **jsfritz said:**
> As I've said, the issues started before I installed dnsmasq, so dnsmasq isn't causing any problems.

your computer -> query opendns server -> opendns server responds -> your computer is happy

i dunno what dnsmasq does. you mentioned dns lookups are slow, that's why I mentioned opendns.

---

### Post by jsfritz on 2006-10-26
Well, I'd like to fix the problem instead of working around it, although opendns may work.  dnsmasq is a local dns server you can run on your computer that caches dns entries.  set network config to look for localhost first, and you wait less for dns resolution.

---

### Post by navlelo on 2006-10-26
Is it possible that this problem is related to the one in [this thread](http://www.ubuntuforums.org/showthread.php?t=283992)? (See my post on page 2).

This may be a shot in the dark, but I think it sounds a bit similar. Bear in mind, I'm a Linux newbie.

---

### Post by stream303 on 2006-10-28
Could be a DNS issue.  What does your /etc/resolv.conf file look like?

Is the first nameserver listed that of the dns server in your router or that of your ISP?  Long delays can sometimes be due to the router dns address being the first one listed.  There is a fix, but lets look here first.

---

### Post by jsfritz on 2006-10-28
I'm not connected to a router, so I would assume it's the ISP DNS server.

---

