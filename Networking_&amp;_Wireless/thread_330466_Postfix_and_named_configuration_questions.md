---
title: "Postfix and named configuration questions"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by showe1966 on 2007-01-03
Hi,

I am trying to set up my computer (running 6.06LTS) as a mail server and a web server.
I only have one computer hence 1 IP address, and I'd like to keep it that way as I believe in simplicity.
I have kludged up my settings on the internet with some kind of tool from my isp since a few weeks now, but I'd really like to know what is actually happening due to my perverse thirst for knowledge and also because i didn't get the mail server working yet.
What I'd like to know is can my mail server and my web server have the same IP address?
That is to say my zone file (FYI located in /etc/bind/)will perhaps look something like below. 
Also, any idea what i can use for my 2nd name server ???
my isp seems to have some to use, but they don't seem to work right.

BTW there is a neat site to check your DNS setup:[http://www.dnsreport.com](http://www.dnsreport.com)

*****************************************************************
@ IN SOA server1.sdi-fabsurplus.com. root.localhost. (
2007010205 ; serial, todays date + todays serial #
28800 ; refresh, seconds
7200 ; retry, seconds
604800 ; expire, seconds
86400 ) ; minimum, seconds
;
NS server1.sdi-fabsurplus.com. ; Inet Address of name server 1
NS ns0.sdi-fabsurplus.com. ; ?? don't know what to put here as i only have one ip address
;

MX 10 server1.sdi-fabsurplus.com.;
MX 20 mail.fabsurplus.com.;
;
sdi-fabsurplus.com. A 88.198.19.46
www A 88.198.19.46

server1 A 88.198.19.46
ns0 A 88.198.19.46 : ?? don't know what to put here really

ftp CNAME www.
****************************************************************************

---

### Post by showe1966 on 2007-01-03
Urg I hate replying to my own posts.
Anyway, apparently , it is okay to have your mail server and web server at the same ip address.

So, now I have another question:-

If I am using a nameserver not at my ip address that is not even having the same domain name as me, do I have to add an A record for this secondary name server or not ?
And what can I do to my settings to prevent use of my DNS server as an open replay, especially if the secondary name server I am going to have to use (managed by my ISP) is an open relay ?
I think I have to put some limits in my named.conf file.

C'mon you brains out there..or I will end up having to answer all the questions myself in a not-very accurate way.

---

