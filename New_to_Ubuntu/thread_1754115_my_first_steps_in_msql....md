---
title: "my first steps in msql..."
date: 2011-05-09
forum: New to Ubuntu
---

### Post by werty2010 on 2011-05-09
what would i need to install-use for my first steps in msql?
any recommendations?

---

### Post by jamesjenner on 2011-05-09
Hey mate,

I presume you mean mySQL? mSql is a commerical product from an Australian company, while mySQL is kinda freeish (though I stopped using them as their licensing got more and more restrictive).

If you do mean mySQL well someone recently posted a real nice guide on how to install LAMP, which stands for Linux, Apache, MySQL and PHP. 

I'm not sure why you wish to install mySQL, but if you wish to use it with Apache and PHP then a LAMP guide is what you need. I did a search for the LAMP guide but cannot find it now sorry.

I'm not on linux at the moment but I'm pretty sure if you just type in MYSQL for the software manager tool then it should come up. Otherwise just google LAMP install (first link is [http://www.lamphowto.com/](http://www.lamphowto.com/)) and that should help.

If you have 11.04 you can have a gander at [http://blog.sudobits.com/2011/04/23/how-to-install-mysql-on-ubuntu-11-04/](http://blog.sudobits.com/2011/04/23/how-to-install-mysql-on-ubuntu-11-04/)

---

### Post by werty2010 on 2011-05-09
you were right.. i mean mysql
i recently started this in school and i just want to start with the very basics..(absolute beginner)
so any  recommendations by someone with some kind of experience?

---

### Post by jamesjenner on 2011-05-09
> **werty2010 said:**
> you were right.. i mean mysql
i recently started this in school and i just want to start with the very basics..(absolute beginner)
so any  recommendations by someone with some kind of experience?

Well I've used mysql quite a lot over the years with both Java GUI based applications and PHP. 

Installing is as simple as following what I posted above.

To use it, well it depends on what you wish to do. Do you wish to use it as a part of a web based project using PHP, or maybe you wish to use it via Java and JDBC or maybe you wish to do some work in C++. Unfortunately we need to know what it is you wish to do, not just the fact that you wish to use mySQL.

Btw, googling "11.04 Mysql" will give you a wealth of information. doing the same for "10.10 Mysql" will give you just as relevant information.

:edit:

I should note that by just installing the software you do get a 'shell' which lets you use sql. That may be a good point to begin. Just install it and type in "mysql" that should give you the shell for mysql. Then you can start using the sql commands. You next need to go to the mysql website and read up on how to manage tables from the shell. This is far better than using a GUI tool as this way you learn how things are being done. Reading up on SQL in general will be very helpful while being aware of specific commands in MySQL.

---

