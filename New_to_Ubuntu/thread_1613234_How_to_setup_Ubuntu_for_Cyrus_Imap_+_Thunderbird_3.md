---
title: "How to setup Ubuntu for Cyrus Imap + Thunderbird 3"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by dom_madrid on 2010-11-04
Hi,

Sorry to bug everyone, but I am stuck with what is probably a simple newbie error.

I've been playing with Ubuntu server 10.04. Got it working internally (samba, cups,...), even got the apache and web sites setup correctly.

My next step was to setup a mail server.
So I followed a very nicely done howto to get postfix + cyrus working. No need to tell me to use dovecot instead, I wanted cyrus to be able to install sogo later on with the least amount of problems.

I also installed roundcube for webmail access.
So far so good. I got incoming mail, outgoing mail, well everything you expect from a mail server. That is... with roundcube.

When trying to connect though a Thunderbird 3, no luck.

I know the mail server works... it works with the webmail part - at the office and outside of the office.  It also works with TB3 when using the internal IP address of the server on the LAN. But no way to get it working with a domain name. 

So I figure the problem was with the connection to the server and the resolution of the server name etc... (/etc/hosts, hostmane, or whatever over config file and anything in between the server and the domain provider)

Can somehow help me to solve that part ?

Thanks in advance,

Dom

---

