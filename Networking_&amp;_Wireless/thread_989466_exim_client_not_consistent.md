---
title: "exim client not consistent"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by eotakos on 2008-11-21
Hi! i'm using exim as a client to connect to a smarthost and sent emails. The connection is encrypted and sometimes everything works just fine and sometimes exim doesn't give the right answer resulting to failure.

this the interesting part of the verbose output when everything works fine:
 
> 
....................................
  SMTP>> STARTTLS
  SMTP<< 220 2.0.0 Ready to start TLS
  SMTP>> EHLO localhost
  SMTP<< 250-mx.google.com at your service, [XXX.XXX.XXX.XXX]
         250-SIZE 35651584
         250-8BITMIME
         250-AUTH LOGIN PLAIN
         250 ENHANCEDSTATUSCODES
  SMTP>> AUTH PLAIN ****************************************
  SMTP<< 235 2.7.0 Accepted
  SMTP>> MAIL FROM:<user@home> SIZE=1429 
..................................


this is the same part of the verbose output when the mail isn't sent
> 
.......................
  SMTP>> STARTTLS
  SMTP<< 220 2.0.0 Ready to start TLS
  SMTP>> EHLO localhost
  SMTP<< 250-mx.google.com at your service, [XXX.XXX.XXX.XXX]
         250-SIZE 35651584
         250-8BITMIME
         250-AUTH LOGIN PLAIN
         250 ENHANCEDSTATUSCODES
  SMTP>> MAIL FROM:<user@home> SIZE=1406
  SMTP<< 530-5.5.1 Authentication Required. Learn more at
.......................


it seems like when exim is supposed to send the login data, it sends other information instead! I have found no consistency to this error. Anyone else had any similar problems?

Any help or ideas are highly appreciated, thanks in advance

---

