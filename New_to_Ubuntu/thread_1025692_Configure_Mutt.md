---
title: "Configure Mutt"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Frank_F on 2008-12-30
Hello,

Wondering if there is any documentation on how to configure Mutt so that I can send e-mail via the command line.


Thanks

---

### Post by billgoldberg on 2008-12-30
This might help.

[http://cuasan.wordpress.com/2008/03/28/setting-up-email-with-mutt-on-ubuntu/](http://cuasan.wordpress.com/2008/03/28/setting-up-email-with-mutt-on-ubuntu/)

---

### Post by Bachstelze on 2008-12-30
You don't need mutt if you just want to send mail.

```
echo "This is a test message." | mail -s "Test message" someone@somewhere.tld
```

---

### Post by Frank_F on 2008-12-30
I tried echo "This is a test message." | mail -s "Test message" [email]someone@somewhere.tld[/email]

and received


the program mail can be found in the following packages

mailutilis
heirloom-mailx

so if download these packages...do i need to configure to an smtp server. or will the command above work ?

Thanks

---

### Post by Bachstelze on 2008-12-30
> **Frank_F said:**
> I tried echo "This is a test message." | mail -s "Test message" [email]someone@somewhere.tld[/email]

and received


the program mail can be found in the following packages

mailutilis
heirloom-mailx

so if download these packages...do i need to configure to an smtp server. or will the command above work ?

Thanks

Whether this will work right away or need tweaking depends on a lot of things. Where is the machine from which you want to send mail located? Home machine? Dedicated server?

---

### Post by Frank_F on 2008-12-30
just my home machine

---

### Post by Bachstelze on 2008-12-30
> **Frank_F said:**
> just my home machine

Okay, then the easiest way is to use [font="monospace"]ssmtp[/font] to send mail through your ISP's mail server. The configuration is simple, but there's a page about it in the [FreeBSD Handbook](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/outgoing-only.html) if you're lost.

---

### Post by Frank_F on 2008-12-30
thanks

---

