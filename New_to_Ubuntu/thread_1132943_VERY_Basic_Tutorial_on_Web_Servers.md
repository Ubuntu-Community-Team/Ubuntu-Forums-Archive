---
title: "VERY Basic Tutorial on Web Servers"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by CostaRica on 2009-04-22
Hi.  I am developing an app in Django, and I want to begin understanding how to deploy it, but I found it to be a very difficult topic!

Please consider that I am posting this in the Absolute Beginner Talk.  Just in order for you to understand my ignorance, only a couple of day ago I began digging into this topics:

- That nginx is a web server like apache
- That static dynamic files are treated differently
- How to connect to my personal Ubuntu Server through ssh to configure it
- Trying to understand the VERY BASICS of Apache and how to configure it

What I need is to be pointed to a VERY VERY BASIC tutorial on web servers (or a book I can buy).  I started to read the apache docs, but could not find the "this is for you, who hardly know what a web server is" documentation.

Thanks in advance!

---

### Post by cariboo on 2009-04-22
It depends how you want to set up your web server, if you intend to install it. If you just need to test your application and don't intend to setup a seperate computer. You can install the LAMP stack on your computer by going to System-->Administration-->Synaptic Package Manager-->Edit-->Select Packages by Task, select LAMP and click apply. This will install Apache2, Mysql and Php5. To administer your server, I would suggest [Webmin]("http:///www.webmin.com/").

---

### Post by CostaRica on 2009-04-22
I already have an Ubuntu server that I installed with the LAMP option, and I am connecting through ssh.  For what I have read, the best way to deploy django is with:
- Apache for the Django dynamic files
- nginx for static files
- mod_wsgi to interpret the python code
- memcached for performance
- Postgresql as database
- psycopg2 as the python-postgresql adapter

all of which are installed.  I visit the static IP a forwarded with my Untangle server and it shows the "It works" message, but I have the following questions:

- How do I know if is it the apache of nginx that responded.
- How do I tell apache where the dir where the Django app is in.
- How do apache and nginx interact (how do they know when each is "in charge" of the HTTP response?

Thanks cariboo907

---

### Post by WorldTripping on 2009-04-22
If you already have a LAMP stack then you already have both a web server and a database.

From what I read, nginx is just a HTTP server. So is Apache so there is no need for both.

Postgresql is a database. So is mySQL which you already have as part of your LAMP installation. Why not use that (OK personal preferences aside).

It looks like you can just install Django on your existing 'out of the box' stack, without all of the unnecessary headaches.

This tells Apache where to look for the Django:
[http://docs.djangoproject.com/en/dev/howto/deployment/modpython/]("http://docs.djangoproject.com/en/dev/howto/deployment/modpython/")

This is how to deploy Apache and Django:
[http://www.djangobook.com/en/1.0/chapter20/]("http://www.djangobook.com/en/1.0/chapter20/")

Either way you'll have to install mod_python into your Apache build:
[http://ubuntuforums.org/showthread.php?t=91101]("http://ubuntuforums.org/showthread.php?t=91101")

Have Fun !

---

### Post by CostaRica on 2009-04-22
The thing is that the Django developers say that postgresql works better with django, but, the database is not a problem, after all.

They talk about using mod_wsgi instead of mod_python (works faster), and nginx for static files and apache for the django dynamic files.

---

### Post by CostaRica on 2009-04-22
Bump.

---

