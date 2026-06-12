---
title: "I want a Database but have no idea whatsoever"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by webmiester on 2009-06-13
Hi,

I dont have any experience in database programming and I dont know any programming language that well.

I'ld like to make a few databases and Ive looked around our installer...

I found Glom which looks very promising and the Database of Openoffice.

Now in their description of Glom, it says something about postgresql.  Do I ned to install that too?  Will I need to load it everytime before loading the database?

Also, the description of openoffice says that mysql and postgre sql will have added funstionality...  will I need to install those too?  Thanks so much.

Ive installed both the database of openoffice and Glom, btw.  But I havent really figured them out.  Thanks

---

### Post by TeoBigusGeekus on 2009-06-13
What do you need to do with the database?
Will it be a simple and small database, which will be operated by ignorant people who need a gui? In that case, openoffice database will be sufficient.
Will it be an online database, or a database operated via another language? Mysql rocks in that case.

---

### Post by Mornedhel on 2009-06-13
Base from OpenOffice for very basic applications. Similar to MS Office's Access, though I've heard the latter is much more feature complete.

MySQL for ease of use and multiple users connected.

PostgreSQL for complexity and power, and multiple users connected.

SQLite3 for great ease of use, but only if only one user needs to be connected at a time.

---

### Post by cariboo on 2009-06-13
To answer your question about GLom, postgresql is listed as a dependency, so it will get installed if you install Glom. I haven't installed postgresql for years, but I always found mysql much easier to setup and work with.

---

### Post by QIII on 2009-06-13
I use postgreSQL for high end database-centric applications for clients (and myself, just because) where there will be multiple connections and high usage.  You will need to be familiar with databases, and getting into it after set up is not intuitive -- even the owner can't get in until some commands are run in the terminal.  Not difficult, but not intuitive.

MySQL is great for small databases for one-off applications and limited connections.  It is very simple to set up and use.

OOo Database is good for simple use with a very limited number of connections.  If you want to write code to support it (beyond macros), you need the OOo Basic SDK.

---

### Post by ayenack on 2009-06-13
My advice would be to install a virtual machine using VirtualBox or such like use the ubuntu server [ubuntu jeos-8.04.1-jeos-i386.iso]("http://cdimage.ubuntu.com/jeos/releases/8.04/release/") and then practice on that. And read every internet how-to on setting up database's. Maybe buy a few books on the subject.

Check this out for a guiding hand on what to buy.

[http://matthewhelmke.net/2009/05/30/reading-up-on-sql/](http://matthewhelmke.net/2009/05/30/reading-up-on-sql/)

---

### Post by jflaker on 2009-06-13
> **webmiester said:**
> Hi,

I dont have any experience in database programming and I dont know any programming language that well.

I'ld like to make a few databases and Ive looked around our installer...

I found Glom which looks very promising and the Database of Openoffice.

Now in their description of Glom, it says something about postgresql.  Do I ned to install that too?  Will I need to load it everytime before loading the database?

Also, the description of openoffice says that mysql and postgre sql will have added funstionality...  will I need to install those too?  Thanks so much.

Ive installed both the database of openoffice and Glom, btw.  But I havent really figured them out.  Thanks

The first order of business is to figure out what you want to do (What data are you going to store -- CD collection, book collection, a private address book, etc?

Next order of business is to understand data normalization -- there are plenty of tutorials, just google "data normalization"


After that, you would need to understand programming.  A PHP web interface would be most portable.

You may want to look at a few books:
[http://www.amazon.com/Beginning-MySQL-Database-Design-Optimization/dp/1590593324/ref=sr_1_1?ie=UTF8&s=books&qid=1244919376&sr=1-1](http://www.amazon.com/Beginning-MySQL-Database-Design-Optimization/dp/1590593324/ref=sr_1_1?ie=UTF8&s=books&qid=1244919376&sr=1-1)

and any one of these....make sure that they are not too far over your head before purchasing
[http://www.amazon.com/s/ref=nb_ss_b?url=search-alias%3Dstripbooks&field-keywords=mysql+php&x=0&y=0](http://www.amazon.com/s/ref=nb_ss_b?url=search-alias%3Dstripbooks&field-keywords=mysql+php&x=0&y=0)

---

### Post by QIII on 2009-06-13
Ah! Normalization.

Just remember:  Maximize normalization for design, selectively denormalize for performance.

Sixth Normal Form is great in theory.  Not so great in practice.

---

