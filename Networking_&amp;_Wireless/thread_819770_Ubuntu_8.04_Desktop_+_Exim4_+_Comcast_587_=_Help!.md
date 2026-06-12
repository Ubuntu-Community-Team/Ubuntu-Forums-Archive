---
title: "Ubuntu 8.04 Desktop + Exim4 + Comcast 587 = Help?!?"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by TheShniz on 2008-06-05
As in the title, I'm using Ubuntu 8.04 Desktop with Exim (the default MTA)... and for the life of me, I can't figure out how to get the mail server working with Comcast's blocking port 25, using port 587, and requiring authentication.


1.)


I've run this, following prompts and made non-split file...

```
sudo dpkg-reconfigure exim4-config
```

I've added to /etc/exim4/passwd.client for SMTP-AUTH as recommended...

```
smtp.comcast.net:username:password
```

I've even tried adding to /etc/exim4/exim4.conf.template to remove the TLS requirement...

```

MAIN_TLS_ENABLE =yes
AUTH_SERVER_ALLOW_NOTLS_PASSWORDS = yes

```

What am I doing wrong, or what else is needed?


2.) 


There is no exim.conf located anywhere, should I create one and bypass Exim's "magic"?  Everything I've read tells me not to, but is it my only choice, or no? (note: [http://polyergic.livejournal.com/](http://polyergic.livejournal.com/))


Help?!?
 - J

---

### Post by TheShniz on 2008-06-06
Bumpity

---

### Post by hackeron on 2008-11-23
anyone? - same problem.

---

### Post by rafiks on 2009-03-25
I have the same problem .. I tried your solution also but it did not work so I gave up and tried postfix .

At first ,I tried setting relayhost = smtp.comcast.net without port 587 but comcast is really blocking port 25 so I had to set it to relayhost = smtp.comcast.net:587..

You also had to setup smtp-auth otherwise comcast will not allow you to send your email. Jus follow this [http://freelock.com/kb/Postfix_relayhost]("http://freelock.com/kb/Postfix_relayhost"). Basically you just need to set up your username and password to login to the relay.

HTH...

---

