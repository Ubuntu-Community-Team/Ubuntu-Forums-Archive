---
title: "Screwed my apache webserver"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by arun chauhan on 2009-12-07
Hi guys, i wanted to have a dyndns site and i got all the formalities done, like setting up modem for dyndns site and a ddclient running..... but was not able to connect to my site....
So i thought i will have to activate my new site on my apache web server..... I really don't know but this thing ruined my apache..... now i have apache running but really of no use....

First thing, what i thought was correct or not??? If yes can you guide me to do it correctly(in case i have done it wrongly) ???

Second thing, How to bring back the apache to it's default stage i.e. when you type
[http://localhost/](http://localhost/)     
a message saying "it works" flashes....


THANKS IN ADVANCE......

---

### Post by sandyd on 2009-12-07
the files that are served by the server are supposed to be in /var/www/ just change the files there

---

### Post by bodhi.zazen on 2009-12-07
> **arun chauhan said:**
> Hi guys, i wanted to have a dyndns site and i got all the formalities done, like setting up modem for dyndns site and a ddclient running..... but was not able to connect to my site....
So i thought i will have to activate my new site on my apache web server..... I really don't know but this thing ruined my apache..... now i have apache running but really of no use....

First thing, what i thought was correct or not??? If yes can you guide me to do it correctly(in case i have done it wrongly) ???

Second thing, How to bring back the apache to it's default stage i.e. when you type
[http://localhost/](http://localhost/)     
a message saying "it works" flashes....


THANKS IN ADVANCE......

LOL

That sounds like the default setup for apache.

My advice is, do't panic, can you describe what you did, step-by-step and what your configuration looks like ?

My guess is that you are working with virtual hosts, which is fine =)

If so, you want to browse to your server name, not [http://localhost](http://localhost)

See also :

[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

