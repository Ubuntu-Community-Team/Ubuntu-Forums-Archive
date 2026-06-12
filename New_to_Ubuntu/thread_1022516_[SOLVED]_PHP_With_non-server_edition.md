---
title: "[SOLVED] PHP With non-server edition"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by WASHAD on 2008-12-26
Now that I'm making the Ubuntu switch, I'm looking at alternatives to ASP.NET. 

I wanted to try PHP and Perl but am having problems with the basic 'hello world' program. 

I'm wondering, does the regular (non-server) version of Ubuntu support PHP for testing purposes? If so, what do I need to type into the browser to link to a web page that I place say...on my desktop. 

Thanks,

SteveJ

---

### Post by jflaker on 2008-12-26
> **WASHAD said:**
> Now that I'm making the Ubuntu switch, I'm looking at alternatives to ASP.NET. 

I wanted to try PHP and Perl but am having problems with the basic 'hello world' program. 

I'm wondering, does the regular (non-server) version of Ubuntu support PHP for testing purposes? If so, what do I need to type into the browser to link to a web page that I place say...on my desktop. 

Thanks,

SteveJ

Have you used Synaptic Package Manager (System, Administration, Synaptic Package Manager)

Select:
MySQL
PHP5
Apache2
phpmyadmin

Point your browser to [http://localhost](http://localhost)
Your files are in /var/www.  You may need to change the permissions on the www folder and files so you can write to them....not sure how, just ask.


It all works.......Server edition just happens to come with that stuff.

---

### Post by albinootje on 2008-12-26
> **WASHAD said:**
> Now that I'm making the Ubuntu switch, I'm looking at alternatives to ASP.NET. 

I wanted to try PHP and Perl but am having problems with the basic 'hello world' program. 

I'm wondering, does the regular (non-server) version of Ubuntu support PHP for testing purposes? If so, what do I need to type into the browser to link to a web page that I place say...on my desktop. 


It comes down to the following :
You need to install apache2 + php5, configure it properly, and then put a php-file in /var/www, then try : [http://localhost/your_file.php](http://localhost/your_file.php) e.g.

These two links could be useful :
[https://help.ubuntu.com/8.04/serverguide/C/php5.html](https://help.ubuntu.com/8.04/serverguide/C/php5.html)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by WASHAD on 2008-12-26
Thanks guys, looks like what I'm hearing is that I need to turn my Ubuntu into a Server edition by running Apache and associated components. 

SteveJ

---

### Post by albinootje on 2008-12-26
> **WASHAD said:**
> Thanks guys, looks like what I'm hearing is that I need to turn my Ubuntu into a Server edition by running Apache and associated components. 


Luckily you don't need to reinstall with the Server install cdrom.
It's all there for you to install now, unless you will put your machine in a server-rack at some webhosting company, you're on the right track already.

Linux = flexible :)

---

### Post by WASHAD on 2008-12-28
Awesome, I'm pretty sure that I can't do that with Windows :)

---

### Post by WASHAD on 2008-12-28
> **jflaker said:**
> Have you used Synaptic Package Manager (System, Administration, Synaptic Package Manager)

Select:
MySQL
PHP5
Apache2
phpmyadmin




Forgive the ignorance -- These programs don't seem to be in my list for Synaptic. I was able to install apache with 'sudo apt-get install apache2', but it can't seem to find MySQL (sudo apt-get install MySQL). 

SteveJ

---

### Post by albinootje on 2008-12-28
> **WASHAD said:**
> Forgive the ignorance -- These programs don't seem to be in my list for Synaptic. I was able to install apache with 'sudo apt-get install apache2', but it can't seem to find MySQL (sudo apt-get install MySQL). 

```

apt-cache search mysql|grep server (as an example to search for something)
sudo apt-get install mysql-server php5 phpmyadmin

```

---

### Post by bodhi.zazen on 2008-12-28
The terms "edition" can be confusing. At the core it is all the same OS and just as you can install KDE applicaitions on Ubuntu (or all of Kubuntu) you can install "desktop" apps on the server and server apps on the desktop.

The server edition comes without X (no graphical interface), the kernel is optized for server functions, and the default applications are different (apache, mysql, etc rather then Gnome). You can customize your ssystem post install.

---

