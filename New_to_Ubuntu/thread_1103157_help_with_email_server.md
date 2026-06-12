---
title: "help with email server"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by frankups1 on 2009-03-22
i am have trouble sending/receiving email on my webserver. i have dovecot sendmail and postfix. i can send mail usuing postfix but when i check the email in gmails it says its from my [email]username@mydomain.hsd1.pa.comcast.net[/email]. i am guessing this is why i am unable to send mail to [email]username@mydomain.com[/email] does anybody know why this is happening?
thank you

---

### Post by cmnorton on 2009-03-25
My experience is from sendmail, so you'll have to map over to postfix.

All our linux servers define a smart host, so that email from them appears to be coming from the domain. The SMART_HOST defines our domain's email server, and the MAQUERADE_AS basically says the email is coming from the same domain as our email server.

define(`SMART_HOST',`esrv.our_domain.com')dnl
MASQUERADE_AS(`our_domain.com')dnl

---

