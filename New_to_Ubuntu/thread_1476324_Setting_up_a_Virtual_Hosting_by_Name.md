---
title: "Setting up a Virtual Hosting by Name"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by macmike on 2010-05-07
Ok, I have my Web Server being able to be seen by the world. My domain name pointing at it right now is [www.wilmingtoncoc.com](www.wilmingtoncoc.com). Nothing in it yet. It is forwarded to my IP address for now. What I want to do is host three things on this server. 2 Websites and an mailing list. I will also need to be able to do CGI scripts with one site. I read what I need to configure to get the Virtual Hosting. It wants what is a DomainRoot. I tried to use mkdir /www/wilmingtoncoc.com and I get an error message back. How do I make this DomainRoot and then once that is done how do I FTP or get the Web files over from another computer to this server? Thanks in advance. I feel I have come a ways at least I can see it from the internet. I know I will have to set up DynDns at some point.

Mike Hughes

---

### Post by madjr on 2010-05-07
did you install ubuntu server or LAMP ?

---

### Post by macmike on 2010-05-07
Started out with Ubuntu 10.04 desktop and then installed the server files.

---

### Post by Ocxic on 2010-05-07
a domain root is the root directory that will have all the files for you website.

eg: /var/www

---

