---
title: "Can't send in Evolution"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by camelface on 2011-01-30
Hey guys, 

So I've been trying to set up a hotmail and gmail account on Evolution. Both see incoming emails but cannot send. I have followed these procedures ([http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/](http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/)) and it has not changed anything. 

I am using pop to recieve and smtp to send with hotmail. 

and

imap to recieve and smtp to send with gmail 



If anyone could help I would appreciate it.

---

### Post by ebasa on 2011-01-30
for hotmail: server:smtp.live.com:587
use TLS encryption
authentication-plain

don't use gmail so no idea

---

### Post by natpat on 2011-02-02
Yeah, I had a problem with this too until a while ago. This set-up works:

Server: smtp.live.com:587
(the :587 on the end made it work)
Use Secure Connection: TLS encryption
Authentication: Login
Username: your full email (example@hotmail.com)

---

### Post by lanzi on 2011-02-02
As for Gmail, use the SSL/TLS Encryption:

Outgoing: smtp.googlemail.com
Port: 465

Incoming: imap.googlemail.com
Port: 993

Works perfectly, in Thunderbird at least.

---

