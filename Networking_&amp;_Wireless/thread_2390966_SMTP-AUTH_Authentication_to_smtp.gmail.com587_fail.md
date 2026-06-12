---
title: "SMTP-AUTH: Authentication to smtp.gmail.com:587 failed"
date: 2018-05-04
forum: Networking &amp; Wireless
---

### Post by merexexchange on 2018-05-04
Hi!

I try to send an email via gmail using sendemail:

sendemail -f [EMAIL="xxxx@gmail.com"]xxxx@gmail.com[/EMAIL] -t [EMAIL="xxxx@gmail.com"]xxxx@gmail.com[/EMAIL] -u subject -m "xxxx" -s smtp.gmail.com:587 -o tls=yes -xu [EMAIL="xxxx@gmail.com"]xxxx@gmail.com[/EMAIL] -xp xxxx
and got:


sendemail[14154]: ERROR => ERROR => SMTP-AUTH: Authentication to smtp.gmail.com:587 failed.

Basically I just want to check if it is possible to send an email from this VPS at all, because after deployment our application started to throw mail auth exceptions.

Would appreciate to any suggestion!

---

### Post by ank2 on 2018-05-04
I don't know Sendmail using Postfix. But remember struggling to get it work with Gmail. IIRC does it has to point at a certificate and also use SASL.

---

### Post by merexexchange on 2018-05-09
The problem has been solved easily ) you just have to install mutt and login with IMAP ) Then you might use SMTP

---

