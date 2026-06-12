---
title: "Integrate Mail"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by jayk121121 on 2007-07-27
Right now I can send mail from my system (jay@jaydesktop.com) to an external email (eg: @gmail.com @yahoo.com etc.).  Is there any way I can receive mail on that address?

---

### Post by dmizer on 2007-07-28
you'll need several things that are too complex to quickly post detailed instructions.

1) you'll need a mail exchanger (properly configured pop server on your ubuntu machine).

2) you'll need a public domain name (like www .your-domain-here.com). probably best way to do that is by setting up a free account with dyndns ( [www.dyndns.com](www.dyndns.com) ).  you'll get a dyndns specific sub domain, so your address will look something like jay(a)desktop.dyndns.com but it's free and there's about 50 subdomains for you to pick from.

3) properly configured NAT with port forwarding to send incoming requests on port 110 to  your mail server.

4) a very security concious thought process.  mail servers are a target for spammers.

there's probably more that i'm missing because i've not yet done this.  though i've always intended to just so i at least know how it's done.  if you run across some good tutorials, post 'em.

---

