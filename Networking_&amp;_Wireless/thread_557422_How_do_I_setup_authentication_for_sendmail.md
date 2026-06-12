---
title: "How do I setup authentication for sendmail?"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by trubblemaker on 2007-09-22
I'm pretty sure it's a configuration issue.  The script is working but sendmail isn't, can't send any mail off my machine no matter what I do.

Here`s me typing it in to show all steps:
```
sendmail -tv
From: matt.smith@serot.mine.nu
Subject: test
To: matt.smith@gmail.com
testing test
matt.smith@gmail.com... Connecting to [127.0.0.1] port 587 via relay...
220 lufa.vc.shawcable.net ESMTP Sendmail 8.13.8/8.13.8/Debian-2; Sat, 22 Sep 2007 12:50:21 -0700; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO lufa.vc.shawcable.net
250-lufa.vc.shawcable.net Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<meat@lufa.vc.shawcable.net> SIZE=87 AUTH=meat@lufa.vc.shawcable.net
250 2.1.0 <meat@lufa.vc.shawcable.net>... Sender ok
>>> RCPT To:<matt.smith@gmail.com>
>>> DATA
250 2.1.5 <matt.smith@gmail.com>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
050 <matt.smith@gmail.com>... Connecting to smtp via relay...
050 220 smtp106.rog.mail.re2.yahoo.com ESMTP
050 >>> EHLO lufa.vc.shawcable.net
050 250-smtp106.rog.mail.re2.yahoo.com
050 250-AUTH LOGIN PLAIN XYMCOOKIE
050 250-PIPELINING
050 250 8BITMIME
050 >>> MAIL From:<smith@lufa.vc.shawcable.net> AUTH=<>
050 [COLOR="Red"]530 authentication required - for help go to http://help.yahoo.com/help/us/mail/pop/pop-11.html[/COLOR]050 <smith@lufa.vc.shawcable.net>... Connecting to local...
050 <smith@lufa.vc.shawcable.net>... Sent
250 2.0.0 l8MJoLxT014213 Message accepted for delivery
matt.smith@gmail.com... Sent (l8MJoLxT014213 Message accepted for delivery)
Closing connection to [127.0.0.1]
>>> QUIT
221 2.0.0 lufa.vc.shawcable.net closing connection
You have new mail in /var/mail/meat

```

How do I setup authentication for sendmail?

---

### Post by trubblemaker on 2007-09-22
found the answer:

[http://www.sendmail.org/~ca/email/auth.html#smtpclient](http://www.sendmail.org/~ca/email/auth.html#smtpclient)

watch out for the permissions, I had to use different permissions for 'makemap ...' proceed correctly.

---

