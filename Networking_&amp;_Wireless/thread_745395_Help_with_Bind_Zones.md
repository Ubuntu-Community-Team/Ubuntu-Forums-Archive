---
title: "Help with Bind Zones?"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by quietas on 2008-04-04
I'm trying to figure out Bind. I have a DNS server setup with our domain (domain.com with [www.mail](www.mail), ...) on it and I need a subdomain (zone?) below that for testing (mail.test.domain.com).

Domain.com
[INDENT]- ns1.domain.com
- www ftp mail

test.domain.com (subdomain/zone?)
[INDENT]- ns2.test.domain.com
- www ftp mail [/INDENT][/INDENT]

I've can function well enough in bind with one simple master zone (?), but I'm a bit lost once I get to adding slave zones (right term?). Anyone care to enlighten me a bit? Or better yet drop me a code snippet with an explanation of what the heck it means? ;)

---

### Post by Eiríkr on 2008-04-04
This site might help: 

[HOWTO - Configure Sub-domains (a.k.a subzones)]("http://www.zytrax.com/books/dns/ch9/subdomain.html")

Cheers,

Eiríkr

---

### Post by quietas on 2008-04-04
That one looks simpler than the other tutorial they have at that site for using a seperate nameserver for the sub-domain. That is what I want to do eventually, but for now only 2 systems will be on that subdomain.

---

### Post by quietas on 2008-04-04
Hhm,I added it in along with my other domain info, but it does not seem to work. I restarted /etc/init.d/bind9 but no luck there.


```
; Test Sub-Domain definitions
$ORIGIN test.domain.com.
                        IN      MX      10 mail
; A Records
mail                    IN      A      xxx.xxx.xxx.xxx
ftp                     IN      CNAME   mail
```

---

### Post by Eiríkr on 2008-04-08
What do you mean by "it does not seem to work"?  Is the named daemon process failing out?  Are there any error messages from named in /var/log/syslog?  Or is it that name resolution is failing for the sub-domain?  

I added the following to my zone file:
```
$ORIGIN test.wolkenhafen.org.
zipper.test.wolkenhafen.org.    IN      A       192.168.10.1
```

Then I added the sub-domain to my search settings in /etc/resolv.conf (bold is added text):
```
search wolkenhafen.org [B]test.wolkenhafen.org
[/B]nameserver 127.0.0.1
```
(Also do-able via the GUI - click the network icon, select Manual Configuration, select the DNS tab, make sure the listings under DNS Servers and under Search Domains are correct.)

Any ping or other hostname lookups that use just the hostname ("ftp" in your example) and not a fully qualified domain name ("ftp.test.domain.com" in your example) will append the strings listed in the search field in the resolv.conf file in order to attempt name resolution.  So if you only have "domain.com" in resolv.conf, no resolution attempt will ever try for "test.domain.com".  

Does this make sense?  After changing your /etc/resolv.conf file, do hostnames in your sub-domain resolve correctly?

Cheers,

Eiríkr

---

