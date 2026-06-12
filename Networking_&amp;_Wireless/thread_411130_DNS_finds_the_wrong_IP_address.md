---
title: "DNS finds the wrong IP address"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by Sarteck on 2007-04-16
Well, this isn't an ubuntu-specific problem, I think, so forgive me.

I have some web space that recently had some trouble.  It was on a shared IP address with other web sites, and it appeared one of those sites pissed Google, Yahoo, and MSN off--Gmail, Yahoo, and Hotmail users could not get registration e-mails from my site.  Apparently, we were on a "blocked" list.

I told the people I buy the web space from, and they said they'd move me to another IP address.  I was like, "Okay, cool."

Unfortunately, it now seems like half the time I get the right IP address, and half the time I don't.  THe "right" IP is supposed to be 67.15.172.6, the other one was 67.15.250.9, and the site is sarteck.com.

The web space provider, siteground, says that it must be something on my end, and that the rest of the world is seeing me as the right IP address, and I can only assume they are right.  They gave me instructions on flushing my DNS cache for both Windows and Linux, and said that it should put it right.

It didn't though, and what made it really weird was that the guy on the Windows computer right next to me saw the "right" address while I saw the "wrong" one last night.  This morning, we're BOTH seeing the wrong address.  Yet THIS ([http://www.dnsstuff.com/tools/lookup.ch?name=sarteck.com&type=A](http://www.dnsstuff.com/tools/lookup.ch?name=sarteck.com&type=A)) tells me that I am just imagining the entire thing.  O.o

Anyone have a bit of advice?



As a bit of a post-note, I can still access both IP addresses separate MySQL databases, and that's what freaks me out the most.  I am trying to design a forum system, but if half of the information goes to one server and half to another... well, it won't be a good thing.  >.<

---

### Post by dbott67 on 2007-04-16
I just pinged your site from here and got the updated IP address (which is good).  I'm also guessing that this is a recent change (less than 24 hours or so?).

As a little background, DNS record changes can take anywhere from a few hours (6 or so) to up to 48 hours, depending on the caching of your local DNS servers.  For example, if you have recently visited a site for the first time, your local DNS server may have to lookup the IP address of the server by asking an upstream DNS server.   Eventually, the request will make it to the "authoritative" server and provide the IP address.

However, if you have recently been to the site (hosted on the old IP address) and then the server is moved to the new IP address, many DNS servers will still have a copy of the old IP cached.  It is this that is likely causing the problem.  Most ISP and local DNS servers cache results for 24-48 hours to save lookups.  After this time expires, the DNS server will perform and authoritative lookup and your problems should disappear.

If your company/ISP has multiple DNS servers, then one may have stale results, while the other has updated results.

Sites like DNSstuff.com will ask for authoritative results (not cached).

_** What can you do:**_

1. Verify is your local or ISP DNS server is using cached results by using the command nslookup:

For your local DNS (if you do not specify a DNS server, it will use your local one):
```
dbott@feisty:~$ nslookup sarteck.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Name:   sarteck.com
Address: 67.15.172.6

```For my ISP (I've added 69.49.32.2 between the command & site to lookup):
```
dbott@feisty:~$ nslookup 69.49.32.2 sarteck.com
Server:         sarteck.com
Address:        67.15.172.6#53

Non-authoritative answer:
*** Can't find 2.32.49.69.in-addr.arpa.: No answer

Authoritative answers can be found from:
69.in-addr.arpa nameserver = dill.ARIN.NET.
69.in-addr.arpa nameserver = BASIL.ARIN.NET.
69.in-addr.arpa nameserver = henna.ARIN.NET.
69.in-addr.arpa nameserver = indigo.ARIN.NET.
69.in-addr.arpa nameserver = epazote.ARIN.NET.
69.in-addr.arpa nameserver = figwort.ARIN.NET.
69.in-addr.arpa nameserver = chia.ARIN.NET.
chia.ARIN.NET   internet address = 192.5.6.32
chia.ARIN.NET   has AAAA address 2001:440:2000:1::21
dill.ARIN.NET   internet address = 192.35.51.32
BASIL.ARIN.NET  internet address = 192.55.83.32
henna.ARIN.NET  internet address = 192.26.92.32
indigo.ARIN.NET internet address = 192.31.80.32
epazote.ARIN.NET        internet address = 192.41.162.32
figwort.ARIN.NET        internet address = 192.42.93.32

```An Authoritative can be obtained at your DNS host (67.15.172.6)
```
dbott@feisty:~$ nslookup - 67.15.172.6
> sarteck.com
Server:         67.15.172.6
Address:        67.15.172.6#53

Name:   sarteck.com
Address: 67.15.172.6

```It does appear that all is okay, and that you'll just have to wait a few hours. 

2. Add the new IP and site (or sites: ftp, mail, etc) to your /etc/hosts file (temporarily):
```

67.15.172.6  [www.sarteck.com]("http://www.sarteck.com")
67.15.172.6  host.sarteck.com
```

After a day or 2, remove the entries from the hosts file.

-Dave

---

