---
title: "Firestarter Firewall configuration"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by joeman225 on 2010-05-05
Hi all,  

I've just downloaded the Firestarter firewall tool, and was wondering what is the most secure (yet useable) configuration/policy? 

I'm  currently using a "restrictive by default, white list traffic" policy, and am allowing service/have rules for: HTTP
 HTTPS 
POP3 
SMTP 

Ideally, I'd like to have maximal protection, while allowing myself to do basic things like browse the web, instant message etc. 

Will these settings be sufficient?  

(I'm pretty new to all this, so please no technical jargon, thorough explanations would be super appreciated)  Thanks!

---

### Post by 3rdalbum on 2010-05-05
Just close all (incoming) ports.

There's a difference between incoming and outgoing ports. Firewalls generally block incoming ports, so remote computers can't start a connection with your computer. However, blocking incoming ports does not stop your web browser or instant messenger from being able to start connections with remote computers.

So that's what you want: Block all incoming ports, even "http" and "https" etc. Unless you're running a web server, but from the sounds of it you're not.

---

