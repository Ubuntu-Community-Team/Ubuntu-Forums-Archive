---
title: "postfix - relayhost configuration problem"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by kalinic on 2009-02-16
I've got postfix installed with smtpd on a server thats also a web server.
I am also trying to use this server as a mail server so the php mail() function can be used on the web pages.

So far no emails have come trough so I ploged trough log files, and in /var/log/mail.warn I'm getting:

[COLOR="Red"]Feb 13 13:54:01 STINTR01 postfix/smtp[22155]: warning: relayhost configuration problem[/COLOR]

Postfix is set to: 
General type of mail configuration: 'Internet site' 
System mail name: 'Localhost'
Local networks:  <my server's IP>/32 [fe80::221:9bff:fefb:2847%eth0]/128
Use procmail for local delivery? No

I've been trying to get this thing to work for 5 days now, any help appreciated!

---

### Post by Mickser_52 on 2009-04-01
I've come across your post by accident and I don't know if you have solved the problem or not. I have just sorted out a similar problem setting up a mail server on an imac with postfix and eventually sorted it out be configuring the postfix main.cf and master.cf files correctly. I may be able to help you if you need it

---

