---
title: "postfix, log shows connection timed out"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-06-17
I just installed postfix and I have no problem using it from a terminal and my evolution client, but it will only send message to users within my e-mail domain.

When I try to send messages out, for example to my account on gmail, I get this error in the log.

```


Jun 17 12:49:16 ubuntu postfix/smtp[18245]: connect to gmail smtp-in.l.google.com[64.233.185.27]:25: Connection timed out


```

Anyone know where I can solve this? I set up my postfix system using the documentation on the ubuntu help site: [https://help.ubuntu.com/community/PostfixBasicSetupHowto?highlight=(postfix](https://help.ubuntu.com/community/PostfixBasicSetupHowto?highlight=(postfix))

---

### Post by Geran on 2008-06-18
Any thoughts on this?

---

### Post by Geran on 2008-06-21
help?

---

### Post by artheus on 2009-04-08
I've got the same problem!
And I've gotten the answer "It's because of that you've got a dynamic IP" But right now I am talking to a guy that have gotten it to work on a Dynamic IP. So I'll see if he can help me with this. :)

I'll send answers when my problem gets solved!

Cheers,
Artheus

---

### Post by jamessnell on 2009-07-27
Well crud.. I've got the same issue, I just freakin wanna send some email, jeez.

```
Jul 27 12:55:48 web1 postfix/master[543]: daemon started -- version 2.5.5, configuration /etc/postfix
Jul 27 12:55:48 web1 postfix/qmgr[547]: CAC9DE8488: from=<doc@dawning.ca>, size=305, nrcpt=1 (queue active)
Jul 27 12:56:18 web1 postfix/smtp[550]: connect to aspmx.l.google.com[209.85.199.114]:25: Connection timed out
Jul 27 12:56:48 web1 postfix/smtp[550]: connect to alt2.aspmx.l.google.com[74.125.79.27]:25: Connection timed out
Jul 27 12:57:18 web1 postfix/smtp[550]: connect to alt1.aspmx.l.google.com[209.85.133.114]:25: Connection timed out
Jul 27 12:57:48 web1 postfix/smtp[550]: connect to aspmx5.googlemail.com[209.85.210.7]:25: Connection timed out
Jul 27 12:58:18 web1 postfix/smtp[550]: connect to aspmx4.googlemail.com[209.85.219.1]:25: Connection timed out
Jul 27 12:58:18 web1 postfix/smtp[550]: CAC9DE8488: to=<j@dawning.ca>, relay=none, delay=981, delays=831/0.06/150/0, dsn=4.4.1, status=deferred (connect to aspmx4.googlemail.com[209.85.219.1]:25: Connection timed out)
```

---

