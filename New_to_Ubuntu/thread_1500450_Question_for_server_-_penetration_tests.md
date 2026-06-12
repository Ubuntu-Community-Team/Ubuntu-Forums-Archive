---
title: "Question for server - penetration tests"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by echo.whoami on 2010-06-03
Does anyone know if there is a program or something that can start some penetration tests on your own website and other services your have up and running and show back the results?

---

### Post by wojox on 2010-06-03
Check out [backtrack-linux.org]("http://www.backtrack-linux.org/")

---

### Post by aeiah on 2010-06-03
the first thing someone malicious would do is an nmap scan to see what ports you have open and what weaknesses you have. if everything is safe as far as ports go, they'd probably look at [cross site scripting](http://en.wikipedia.org/wiki/Cross-site_scripting) or [sql injection](http://en.wikipedia.org/wiki/SQL_injection)

they may also try brute-forcing your passwords - just make sure you're using complicated / random ones that are unlikely to show up in a dictionary file (a brute force dictionary i mean)

but anyway, i guess your first step would be to fire up nmap (or zenmap, since it's nice and easy to use) and see what's open on the server.

---

### Post by echo.whoami on 2010-06-03
I have many services running (ssh,proftp,apache,vnc,transmission) and i have found many attempts to break in my server. 

on ssh everyday i find some weird ips from china,us and all over trying to get access. i use denyhosts for this.


i used zenmap and all ports that's open and the services that they running is what i have allowed and i expected to be there. 

i also have some questions:

   1)on ftp i don't have a tool to look at auth attempts and block after some attemps. is there a tool?

   2)on apache i have a site with html,php,mysql and it's very basic with just a form and a page showing the inserts. but today i found out from the logs that something like Comodo-Certificates-Spider has erased all.

what you recommend to do ???????

   3)if i stop apache but not close the port 80 on firewall is there a hole that could someone use?????

Thank you very very much for your time!!!!!!!

---

### Post by echo.whoami on 2010-06-03
does anyone know ?????? please..........

---

### Post by The Cog on 2010-06-03
[http://www.nessus.org/](http://www.nessus.org/) ?

---

### Post by bodhi.zazen on 2010-06-03
OpenVAS is an up and coming option. It is in the Ubuntu repos , takes a while to learn, and there are a few (minor) glitches.

---

### Post by echo.whoami on 2010-06-03
thank you for your directions!!! :)

---

