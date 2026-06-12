---
title: "want to set up an email server"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by wingnut2626 on 2013-09-15
Hi all, I just bought a domain from Godaddy, and want to have my own email server run on that domain.   I have ubuntu server 12.04 running on the machine that I want to be the mail server.  I have been trying tutorials with postfix and dovecot, but nothing seems to be working.  I just want to be able to send & receive email from [email]myname@mydomain.net[/email].  Any help?

---

### Post by TheFu on 2013-09-15
Which network holds your "server?"  A residential ISP probably blocks all SMTP traffic that is not sent through their email gateway.

* Domain - check
* DNS with A, CNAME and MX records?
* Server running an MTA?
* Ability to send on port 25 to anywhere in the world? 
* Ability to receive on port 25 from anywhere in the world?

Postfix is pretty simple for a basic installation. If there are issues, it is likely your network provider.

---

### Post by TheFu on 2013-09-15
forums error - double post.

---

