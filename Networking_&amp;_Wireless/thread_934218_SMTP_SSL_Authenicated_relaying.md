---
title: "SMTP SSL Authenicated relaying"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by sixteensix on 2008-09-30
Hi all,

I have a challenge and I am wondering if it is possible to do. I have an application that requires to send emails and faxes though our corporate email/fax/sms gateway. 

Unfortunately the application is unable to send through this gateway as it requires SSL Authentication (We are badgering the application company to add this as a feature but this could take 12/18 months minimum) 

I was hoping to use postfix as a middle man, that would relay email to the smtp server that can access the fax and sms gateways. Can postfix connect to an SSL smtp server that requires a username and password?

Any comments, opinions or ideas please let me know.

Many thanks

Tim
Sixteensix

---

### Post by sixteensix on 2008-10-01
Sorry...Bump..

---

