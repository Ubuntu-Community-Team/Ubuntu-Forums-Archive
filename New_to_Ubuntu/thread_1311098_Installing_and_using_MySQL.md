---
title: "Installing and using MySQL"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Riffster on 2009-11-02
I've got a database projects that I want to work on and so I've looked at the options open to me and MySQL seems to be pretty favourable (esp since I'm no expert in databases or Linux)

I run 9.04 I think I installed MySQL  but I can't seem to get it to work. I've certainly got the mysql folder in /etc but I can't make head nor tail of the config file - it could be in cuniform for the sense I can make of it. (I'm used to the Windows install that pretty well does it all.) The only other threads on here that come close haven't resolved my problems. 

I'm a self-confessed noob, so any and all advice would be welcome.

---

### Post by stoogiebuncho on 2009-11-07
If you are new to linux and databases, you might be better off with a database that has a graphical front end.  Have you looked at the OpenOffice.org Database program?

MySQL is great and has many applications, most commonly web development alongside PHP, but I believe it's all command line.  So depending on what projects you are working on, a different program may suit your needs better.

---

### Post by ratcheer on 2009-11-07
I am just now doing the same thing, except I am an Oracle DBA with many years of experience.

To install MySQL, you just go to Synaptic Package Manager and search for "mysql". You will get a lot of stuff. Get at least mysql-server-5.1 and mysql-doc-5.0. The documentation should start you on your way.

Tim

---

### Post by Ms_Angel_D on 2009-11-08
There is [phpmyadmin]("http://www.phpmyadmin.net/home_page/index.php") for mysql, it gives you a type of interface to work with.

It's available in the repo's (synaptic) but You'll have to also install apache to use it. You might want to have a look at this page: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by The Cog on 2009-11-08
The programs mysql-admin and mysql-query-browser give you graphical interfaces to mysql. They are in the synaptic repositories. I don't know if they get icons in the start menu - I always start them by pressing Alt-F2 and typing in their name.

When you connect to MySQL you have to give a username and password. For a new install, the only user in the MySQL database is "root". From there, you will probably want to add other users and then grant them some rights such as creating, inserting, deleting etc.

You have to connect to MySQL even when you are on the same machine by the way - MySQL is purely a server. You treat it exactly the same whether you are local or remote except that it won't let user root connect to it remotely.

---

### Post by phillw on 2009-11-08
> The programs mysql-admin and mysql-query-browser give you graphical interfaces to mysql. They are in the synaptic repositories. I don't know if they get icons in the start menu - I always start them by pressing Alt-F2 and typing in their name.

They did in 9.04. I'm guessing they will in 9.10

My install of all things LAMP was from here -->> [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

If the OP has a question about the use of MySQL, I'll answer an IM, but a good place to head over for that stuff is here  ---->  [http://forum.codecall.net/](http://forum.codecall.net/)

If you want database stuff, then it hides here ---> [http://forum.codecall.net/database-database-programming/](http://forum.codecall.net/database-database-programming/)

They are a good set of people and also cover oracle, etc.

For stuff on mysql, how it interacts with php and html, then tizag are pretty good --->> [http://www.tizag.com/mysqlTutorial/](http://www.tizag.com/mysqlTutorial/)

I do have an area of my own for mysql stuff, but it is for the fine-tuning of the powerful search ability, so not really suited for beginners.  If any one wants that link, it's here -->> [http://www.vpolink.com/forumdisplay.php?f=300](http://www.vpolink.com/forumdisplay.php?f=300)

Phill.

---

