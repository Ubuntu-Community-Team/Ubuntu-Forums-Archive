---
title: "Mail Server @ Home over dyndns"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by bikernboy on 2010-08-26
Hi there i am the guy in town, 

I have set up a my own webserver with a help of my friend. This hosted a website over dyndns. On this site i got a contact form which should sent me an email when i hit the sent button. 

in the mail.log i get this message

Aug 26 07:22:48 ubuntu postfix/pickup[11901]: 450834202C0: uid=33 from=<info@latido-volunteering.net>
Aug 26 07:22:48 ubuntu postfix/cleanup[12454]: 450834202C0: message-id=<20100826052248.450834202C0@ubuntu.bob>
Aug 26 07:22:48 ubuntu postfix/qmgr[7017]: 450834202C0: from=<info@latido-volunteering.net>, size=546, nrcpt=1 (queue active)
Aug 26 07:22:49 ubuntu postfix/smtp[12457]: 450834202C0: to=<latido.volunteering@googlemail.com>, relay=gmail-smtp-in.l.google.com[74.125.43.27]:25, delay=1.4, delays=0.11/0.05/0.52/0.7, dsn=2.0.0, status=sent (250 2.0.0 OK 1282800157 a8si2878629fak.76)
Aug 26 07:22:49 ubuntu postfix/qmgr[7017]: 450834202C0: removed

as u see i got postfix installed together with mailx. As a noob i would say this message is sent successfully but in fact there is no mail in mail gmailbox.

hope there is anybody out there who can help me

---

