---
title: "exim4+mail"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by ramboza on 2008-11-18
I'm trying to setup exim4 to be able to send emails to remote addresses via mail command.

I've configured exim4 by dpkg-reconfigure exim4-config
Used [http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html) as a guide.

So i've selected Internet site using smarthost

And entered smtp.mail.ru as a smarthost.

No i've followed this guide:

[http://www.debian-administration.org/articles/280](http://www.debian-administration.org/articles/280)

to setup authentication in smtp.

When i try to :

echo test | mail -s test [email]user@domain.com[/email]

i see this in /var/log/exim4/mainlog :

2008-11-18 21:23:15 1L2VEJ-0000iZ-NR ** [email]user@domai.com[/email] R=smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after pipelined DATA: host smtp.inbox.ru [194.67.23.113]: 503 Administrative prohibition -- authorization required.  Users in your domain are not allowed to send email without authorization. 


So looks like the authorization module is not working at all, i think the log would have given "invalid user/pass" or smth...

Any ideas?

---

### Post by ramboza on 2008-11-18
Bah, solved...

The conf i've made is for exim SERVER side smtp auth :)
For client side you should edit /etc/exim4/passwd.client file.
And add AUTH_CLIENT_ALLOW_NOTLS_PASSWORDS=1 to /etc/exim4/exim4.conf.localmacros 

So it works :)

---

### Post by eotakos on 2008-11-18
the macro command you gave equal to 1 is for not encrypted connections. I've read somewhere in the exim-doc that this way the passwords are send as plain text.

if you are not interested in using the particular smpt server you are using, you could create a gmail account, and use the smtp.gmail.com with the password of the account. This way you have secure connections (uses TLS).

---

