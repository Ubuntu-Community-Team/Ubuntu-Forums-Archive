---
title: "IPv6 problem resolving IPv4-only host (with wget)"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by dmrazor on 2013-12-04
I'm running into a very weird issue on my Ubuntu server 12.04.3 LTS system. It's been set up to also use IPv6 (2001:xxx:yyy:1::12). When using wget to connect to an IPv4-only host the following happens:

```
wget http://www.newznab.com
--2013-12-04 21:22:31--  http://www.newznab.com/
Resolving www.newznab.com (www.newznab.com)... 2001:xxx:yyy:1::12, 5.39.78.35
Connecting to www.newznab.com (www.newznab.com)|2001:xxx:yyy:1::12|:80... 
```

Instead of finding *no* IPv6 address for [www.newznab.com](www.newznab.com), wget DNS resolution finds my *own* IPv6 address first, and the correct IPv4 address second. It then tries to connect to the first address found, which is completely wrong of course. Can anyone shed some light on why this would be happening?

I am running my own nameserver, which afaik is set up correctly. Doing the above name resolution using 'host' doesn't show this strange behaviour:

```
 host www.newznab.com
www.newznab.com has address 5.39.78.35

```

As a work-around I've edited /etc/gai.conf to prefer IPv4, which ensures wget finds the correct address first. But it still finds the wrong address second, which shouldn't be the case imo.

Thanks for any insights,

Raz.

---

### Post by dmrazor on 2013-12-08
SOLVED: I had an incorrect search domain that got added on non-existent lookups, making them appear as if they were part of my domain. And so we learn :D

---

### Post by mennopieters on 2014-02-06
Hi dmrazor,

Today I came across the same issue. I had set the [FONT=courier new]dns-search[/FONT] in [FONT=courier new]/etc/resolv.conf[/FONT] to my personal domain name which has a wildcard A and AAAA-record. Setting the [FONT=courier new]dns-search[/FONT] to my uplink ISP's domain name solved it for me, too, but I'd like to have my system search ***my*** domain correctly. If you have any suggestions, please let me know.

Thanks,

Menno

---

### Post by dmrazor on 2014-02-07
In my case I was searching through 2 domains: a fictitious 'mydomain.lan' (as viewed from 'the inside') and the formal 'mydomain.nl'. Also, I was running my own DNS server for internal use (serving 'mydomain.lan'), which at the time was configured for IPv4 only. I've since set up the DNS server to also support IPv6, reconfigured it to serve only 'mydomain.nl' and have gotten rid of the double search domains in my resolv.conf. Basically: I've simplified my setup as much as possible. That did the trick for me.

Cheers,
Raz

---

