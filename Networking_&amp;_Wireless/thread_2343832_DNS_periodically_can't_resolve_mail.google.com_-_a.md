---
title: "DNS periodically can't resolve mail.google.com - and ONLY that name"
date: 2016-11-19
forum: Networking &amp; Wireless
---

### Post by sorceror171 on 2016-11-19
Very strange behavior. Sometimes I can connect to mail.google.com, but it seems that randomly, DNS suddenly can't resolve that name. What's weird is, no other sites seem to have that issue. I have modified my DNS setup to use Google and OpenDNS servers, instead of my ISP's DNS servers, but everything else works, even other *google.com addresses! In my "Wired connection 1" settings, under "Additional DNS servers", I have "8.8.8.8, 8.8.4.4, 208.67.222.123, 208.67.220.123".

At the moment, I'm having the issue.

```
$ nslookup mail.google.com 
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
mail.google.com	canonical name = googlemail.l.google.com.
```

Other Google sites are unaffected:

```
$ nslookup play.google.com
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
play.google.com	canonical name = play.l.google.com.
Name:	play.l.google.com
Address: 216.58.192.142
```

But what's weird is, if I query mail.google.com and specify the DNS server directly, it works:

```
$ nslookup mail.google.com 8.8.8.8
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
mail.google.com	canonical name = googlemail.l.google.com.
Name:	googlemail.l.google.com
Address: 216.58.192.133

```

It seems to go away after a while - up to half an hour - but needless to say, this is annoying. Anyone have any suggestions?

---

### Post by SeijiSensei on 2016-11-19
I have a local BIND server that connects directly to the root nameservers.  That server returns 172.217.3.5 as the IP for mail.,google.com.  However 8.8.8.8 and 8.8.4.4 return 216.58.219.197 instead.  Despite both being the address of "mail.google.com" neither server accepts SMTP, POP3, or IMAP4 packets! They only expose web services on ports 80 and 443.

How about creating an entry in /etc/hosts that reads
```

216.58.219.197     mail.google.com

```
and pegging the name to just one server address?  If that one proves unreliable, try 172.217.3.5 instead.

---

### Post by sorceror171 on 2016-11-20
> **SeijiSensei said:**
> I have a local BIND server that connects directly to the root nameservers.  That server returns 172.217.3.5 as the IP for mail.,google.com.  However 8.8.8.8 and 8.8.4.4 return 216.58.219.197 instead.

That's because Google plays games with DNS to spread users out among servers that are 'closer' in some way. Someone in Europe querying mail.google.com is going to get a different address than someone in Australia or North America. It's possible those tweaks are messing something up - but I suspect a problem with the default local-caching DNS Ubuntu comes with. As I said, if I query a nameserver directly, bypassing localhost, I get an address.

For now, sticking an address in the hosts file will probably work; but I'd really like to figure out the underlying issue and fix it, in case other addresses give me problems in the future.

---

### Post by sorceror171 on 2016-11-29
Okay, today I got the same behavior with [www.linkedin.com](www.linkedin.com).

```
$nslookup [www.linkedin.com](www.linkedin.com)
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
[www.linkedin.com](www.linkedin.com)	canonical name = any-na.[www.linkedin.com](www.linkedin.com).
```

I do *not* want to have to keep adding lines to /etc/hosts to deal with this. That's a recipe for long-term heartache. I tried running:

```
sudo /etc/init.d/dns-clean
```

...but this had no effect. Is it time to disable the local dnsmasq setup completely? Are there logs I should be looking at, or some way to diagnose the issue?

---

### Post by darren780 on 2016-12-06
mail.google.com has issues with opendns, something related to their parental blocking and it is turned on by default unless you register an account.  People have complained about this for years and you would think at least some google sites would get added to an internal opendns whitelist.  Drop opendns, and you will have no further problem.

Here is a post from 2013 of some people having the same issue, they go into more detail.

[https://support.opendns.com/hc/en-us/community/posts/220023647-gmail](https://support.opendns.com/hc/en-us/community/posts/220023647-gmail)

---

