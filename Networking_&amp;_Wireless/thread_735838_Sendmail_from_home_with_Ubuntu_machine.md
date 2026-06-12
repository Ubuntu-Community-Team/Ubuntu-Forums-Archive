---
title: "Sendmail from home with Ubuntu machine"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by ubuntogenius on 2008-03-26
I want to setup Sendmail from my home Ubuntu PC. I have register.com pointing here at home and I am already hosting a web page with the domain. I want to send emails from this Linux machine if possible. I wonder if sendmail is a good choice as to Qmail.

---

### Post by chilinski on 2008-03-26
Sendmail will work just fine. It's a little easier to configure if you install webmin (a lot of things are easier to configure with webmin). You can also configure QMail through webmin.

You have an MX record and a reverse dns PTR record at register.com for your domain, right?

Another email addon that you might want to look at is mailscanner at mailscanner.info. There's also dovecot, which would allow you to run IMAP and you can do secure IMAP and POP3. And don't forget ClamAV for virus protection and SpamAssassin for spam. Oh, yes, and Bayes... Bayes will help you with your anti-virus efforts.

Email is a wonderful world. And the great part is that it can take up the hours you used to dedicate to sleep.

---

