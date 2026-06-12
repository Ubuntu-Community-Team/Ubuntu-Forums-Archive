---
title: "Email Server that processes mail"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by madman92 on 2008-05-20
Hi everybody,

We want to make a mail server that will automatically process emails when they are recieved. Right now we have a squirrelmail server running on apache. Where should we start?

---

### Post by xkaliburx on 2008-05-20
Squirrelmail is just a mail viewer (running on apache) but there must be a mailserver running on that box, so I am a bit unsure what your setup is.

If you want to start from scratch (and the doc's use squirrelmail also), I would highly reccomend qmail.

2 great, great sites can be found at 
[URL="http://qmailrocks.com"]http://qmailrocks.com/
[/URL] and [http://www.lifewithqmail.org/lwq.html]("http://www.lifewithqmail.org/lwq.html")

Good luck

---

### Post by madman92 on 2008-05-26
So I figured it out. My final setup is with uw-imap. I have a php file that parses the mail in /var/mail and then it spits stuff out, and I have cron running that every minute.

---

