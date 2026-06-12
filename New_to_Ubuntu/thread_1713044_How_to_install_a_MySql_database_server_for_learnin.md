---
title: "How to install a MySql database server for learning purpose on ubuntu 10.10?"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by aniljaiswal on 2011-03-23
As of now, I was using oracle database server installation on windows 7 to learn sql which is a part of my course this semester. But recently I switched completely to linux i.e. Ubuntu 10.10 and now I am finding a little difficult to get things started for MySql to work as it being the only contender to Oracle's windows version of SQL. 
I need a GUI to work on as well. I feel myself stuck most of the times with command line operation as I have been working all my life with snoppy windows GUI interface.
So, help me out with the step-by-step installation of mysql on ubuntu to get things started. 

Thanks

---

### Post by wolfgangmcq on 2011-03-23
To install the mysql server, install the [mysql-server]("apt://mysql-server") package. Just follow the prompts. If you want a gui, install [apache2]("apt://apache2") and [phpmyadmin]("apt://phpmyadmin"). Once those install, go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) (from the computer you installed it on), and log in with user root and whatever password you set when you installed mysql-sever.
Hope this helps!

---

### Post by TeoBigusGeekus on 2011-03-23
Alternatively, you could install MySql Administrator and MySql Query Browser.

---

### Post by Ghost_Mazal on 2011-03-23
MySql workbench is pretty handy too.

---

### Post by The Cog on 2011-03-23
A very different alternative might be to install the sqlite-manager plugin for forefox. This provides a GUI that allows you to work on sqlite database files. Its sql support is very good and the whole database is stored in one file. SQLite is more like a database application than a database server. In my opinion, it's easier to get started with than a full-blown server.

---

### Post by aniljaiswal on 2011-03-23
> **wolfgangmcq said:**
> To install the mysql server, install the [mysql-server]("apt://mysql-server") package. Just follow the prompts. If you want a gui, install [apache2]("apt://apache2") and [phpmyadmin]("apt://phpmyadmin"). Once those install, go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) (from the computer you installed it on), and log in with user root and whatever password you set when you installed mysql-sever.
Hope this helps!
Installation is complete for all the three quoted packages, but I am getting a "404 Not Found' on entering the "http://localhost/phpmyadmin/" address in URL bar. I have configured the root password for MySQL as well as PHPMYADMIN package when prompted. How could this be solved?

---

### Post by aniljaiswal on 2011-03-23
I was able to run mysql through phpmyadmin web interface by making some changes to configuration files as below.

code:
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
sudo /etc/init.d/apache2 reload
Thanks

---

### Post by SeijiSensei on 2011-03-23
> **aniljaiswal said:**
> I am finding a little difficult to get things started for MySql to work as it being the only contender to Oracle's windows version of SQL.

It's sad that so many people think this.  [PostgreSQL]("http://www.postgresql.org/") is an excellent SQL server and totally free.  It has many features that make it competitive with enterprise solutions like Oracle.  I use PostgreSQL exclusively unless I encounter a particular application that demands MySQL.

You can also [install Oracle]("http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html") itself on Linux.  It's not free for commercial use, but the license grants "a nonexclusive, nontransferable limited license to use the programs only for the purpose of developing, testing, prototyping and demonstrating your application, and not for any other purpose."  Your usage as a student clearly falls into this category.

---

### Post by aniljaiswal on 2011-03-24
> **SeijiSensei said:**
> It's sad that so many people think this.  [PostgreSQL]("http://www.postgresql.org/") is an excellent SQL server and totally free.  It has many features that make it competitive with enterprise solutions like Oracle.  I use PostgreSQL exclusively unless I encounter a particular application that demands MySQL.

You can also [install Oracle]("http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html") itself on Linux.  It's not free for commercial use, but the license grants "a nonexclusive, nontransferable limited license to use the programs only for the purpose of developing, testing, prototyping and demonstrating your application, and not for any other purpose."  Your usage as a student clearly falls into this category.



Thanks for the suggestion and as a matter of fact, I installed oracle successfully this morning after failing to work with MySql interface. This goes by saying that, I had been using ORACLE's 10g database express edition on my windows operating system and it worked just fine. Until recently, I switched to linux completely for my full-time operating system I realized that there's a need of a good database system. So I am finally putting my fingers on Oracle. 
But there's something which has not let me start working with the database yet. It's actually that I can't find the link to open the oracle database engine in my browser. It is installed by the name of "Oracle Database Express Edition 10g" in the main Application Menu of Ubuntu, and has sub-categories in it like "help link", "start database", stop database", and most importantly "Go To Database Home Page". This is the link which should take me to the GUI of oracle database server where I would be able to work upon. But as I click on the link, all it does is opens the web browser(default set is Mozilla Firefox in my case) and the Firefox's home page is opened. I can't find any link in the help files either. 
Please help me.

Thanks.[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186954&stc=1&d=1300967671[/IMG]

---

### Post by SeijiSensei on 2011-03-24
You'll need to search the Oracle documentation and forums.  Few people here are probably running Oracle.  The vast majority probably use MySQL, with the rest of us largely running PostgreSQL.  

My only experience with Oracle came from working with a client who had a manufacturing system built on it.  The few times I needed to interact with the server, I used command-line tools.

On the occasions when when I need to use a GUI for some reason to talk to a database server, I run Microsoft Access in a VirtualBox virtual machine and link to the tables stored on my PostgreSQL server via ODBC.

---

### Post by wolfgangmcq on 2011-03-25
> **aniljaiswal said:**
> Installation is complete for all the three quoted packages, but I am getting a "404 Not Found' on entering the "http://localhost/phpmyadmin/" address in URL bar. I have configured the root password for MySQL as well as PHPMYADMIN package when prompted. How could this be solved?

On my computer (Karmic), it worked just fine the first time I started. You may have to restart the apache server (with sudo apache2ctl restart). Make sure you're using the computer you installed phpmyadmin on to access it.

---

