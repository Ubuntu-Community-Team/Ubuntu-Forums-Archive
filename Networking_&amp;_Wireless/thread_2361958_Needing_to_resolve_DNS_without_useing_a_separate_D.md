---
title: "Needing to resolve DNS without useing a separate DNS server"
date: 2017-05-22
forum: Networking &amp; Wireless
---

### Post by chriso0258 on 2017-05-22
Hello,

Our maintenance department uses some software to monitor various maintenance functions. The software will only send alerts via email so I set up a Ubuntu Server with iRedMail on it. It is on a private network with no access to the internet. I have no problems sending  and receiving emails in my test environment because I use the server's IP address. However, the software wants to use DNS (sending it's email alerts to the [email]alerts@maintenance.com[/email] email address I set up). In iRedmail I set up the virtual domain as maintenance.com but I have no DNS server on the private network to resolve this and we don't want to put a separate DNS server on the maintenance network. Is there anyway to configure my Ubuntu server so that when one of the maintenance computers sends out an alert to the [email]alerts@maintenance.com[/email] email address the mail server will actually receive it (if there is an article you can provide a link to that would be helpful as I will need a step by step approach to set it up if it's do-able)

I hope this makes some sense. Thank you for your assistance.

Chris

---

### Post by SeijiSensei on 2017-05-22
First, it depends on what mail program you're using.  With sendmail, you can use the "[virtusertable]("http://etutorials.org/Server+Administration/Sendmail/Part+I+Build+and+Install/Chapter+4.+Configure+sendmail.cf+with+m4/FEATUREvirtusertable/")" to map names of the form somename@somedomain to a local mailbox.  For instance, an entry like
```
alerts@maintenance.com     joe
```
will route all mail for the alerts address to joe's local mailbox.

Postfix has an [elaborate method for virtual hosting]("http://www.postfix.org/VIRTUAL_README.html") that I'm not very familiar with.  Perhaps someone else can help, though I think it's possible to avoid all that as described below.

In either case, you'll need to configure the server to accept mail for "maintenance.com".  In sendmail, that happens in the /etc/mail/local-host-names file.  On Postfix, I believe you would use the "[mydomain](http://www.postfix.org/postconf.5.html#mydomain)" parameter.  If set to "maintenance.com" the server should treat mail it receives for that domain as local and not do an MX lookup out on the Internet.  You may be able to avoid the virtual hosting stuff simply by making this change and creating an account on the box called "alerts" to receive the mail.  Or create an alias in /etc/aliases that maps from "alerts" to a valid mailbox (e.g., "joe") or a mailing list.

One other possibility.  The address "alerts@[10.10.10.10]" is a valid RFC822 address and should be routed directly to the 10.10.10.10 machine without any DNS resolution.  I don't know if IRedMail will accept that as a valid address though. You might need to specify [10.10.10.10] as a supported [destination]("http://www.postfix.org/postconf.5.html#mydestination") to make this work.  (Of course, you'd replace 10.10.10.10 with the IP address of the mail server.)

---

