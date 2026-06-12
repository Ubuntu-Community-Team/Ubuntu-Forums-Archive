---
title: "Please have a look if this means I have MySQL installed"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Ubunser on 2010-05-04
I can't figure if I have it or not. I installed lamp if I'm right and definitely wanted apache php and MySQL all together. But when I type in source [HTML]<?php phpinfo(); ?>[/HTML]it shows

---

### Post by indytim on 2010-05-04
You have it installed.  If you scroll down, you'll see a section denoting the MySQL settings.  You are looking at the configuration data associated with the LAMP server.  If the parts were not installed properly, you would not see this page.

Happy LAMPing

IndyTim / DataMan

---

### Post by Ubunser on 2010-05-04
Also in terminal [HTML]mysql[/HTML] yields 
[HTML]proggist@proggist-laptop:~$ mysql
The program 'mysql' can be found in the following packages:
 * mysql-client-5.0
 * mysql-client-5.1
Try: sudo apt-get install <selected package>
bash: mysql: command not found
proggist@proggist-laptop:~$ 
[/HTML]

---

### Post by Ubunser on 2010-05-04
> **indytim said:**
> You have it installed.  If you scroll down, you'll see a section denoting the MySQL settings. 

IndyTim / DataMan

Like this ha-ha) Than you!

---

### Post by Ubunser on 2010-05-04
Guys, why I can't adress to MySQL via terminal? I get the result I posted above every time I type there <mysql> or <mysqladmin>

---

### Post by Ubunser on 2010-05-05
Help, I can't assign passwords and what's more write commands in mysql programms, cause I have no idea how do I install it, if I have it or not.
This is my thread where I explain what's happening if you haven't got me yet. Please help.
[http://ubuntuforums.org/showthread.php?t=1472167]("http://ubuntuforums.org/showthread.php?t=1472167")

---

### Post by PriceChild on 2010-05-05
> **Ubunser said:**
> Also in terminal [HTML]mysql[/HTML] yields 
[HTML]proggist@proggist-laptop:~$ mysql
The program 'mysql' can be found in the following packages:
 * mysql-client-5.0
 * mysql-client-5.1
Try: sudo apt-get install <selected package>
bash: mysql: command not found
proggist@proggist-laptop:~$ 
[/HTML]
Have you tried following the instructions it suggests?

```

The program 'mysql' can be found in the following packages:
 * mysql-client-5.0
 * mysql-client-5.1
Try: sudo apt-get install <selected package>

```

---

### Post by Ubunser on 2010-05-05
I installed some mysql-server via synaptic. What in the world does it mean that I have to install all mysql"s" I can find. I thought I had it! But I only had mysql-common, that didn't yield anything. I doubt I need it! Than I downloade some mysql 5.0. Still no good. Than I got mysql-server, but now I can't connect to it cause I don't know what login to use. And I have to use the following code for it [HTML]mysql -h host -u user -p[/HTML]

---

### Post by kwacka on 2010-05-05
You might find it easier to use one of the graphical front-ends to MySQL such as PHPmyadmin (in the repositories) or webmin (which isn't but if you do a search you'll find a .deb file to install it.

---

### Post by PriceChild on 2010-05-06
> **Ubunser said:**
> I installed some mysql-server via synaptic. What  in the world does it mean that I have to install all mysql"s" I can  find. I thought I had it! But I only had mysql-common, that didn't yield  anything. I doubt I need it! Than I downloade some mysql 5.0. Still no  good. Than I got mysql-server, but now I can't connect to it cause I  don't know what login to use. And I have to use the following code for  it [HTML]mysql -h host -u user -p[/HTML]
No... read the instructions again :-)

> **PriceChild said:**
> Have you tried following the instructions it suggests?

```

The program 'mysql' can be found in the following packages:
 * mysql-client-5.0
 * mysql-client-5.1
Try: sudo apt-get install <selected package>

```

mysql is provided by those two packages. Choose one.

So for example, run...

```
sudo apt-get install mysql-client-5.1
```

---

### Post by Ubunser on 2010-05-07
Thank you all! I've figured things out. I have been usin the wrong way to connect. I was using my computer root login to connect to mysql, which is wrong because the root user in mysql by default is 'root'. 
Finally, I tested the MySQL, created my first database and table. I even loaded the contents of my first table from .txt file, that I created for this purpose. MySQL looks really simple. Now I have to go bach to PHP to study it.

---

