---
title: "Home web server with php &amp; mysql needed"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by greentrees on 2009-05-01
Hi All,
 
I'm looking to add a home web server to my shiny new 3rd time install of ubuntu 8.04 (not LTS). Before I make any more mistakes and have to start again I thought I'd seek some advice. This is what I think I need...
 
1) A cpanel type interface that will allow me to create multiple sites that I can surf to and ftp to from my windows box via my router. I will modify the hosts file on the windows box to suit so I can surf to [http://mysite.com](http://mysite.com) so I think I may need dns.
 
2) php and mysql are essential, I'd like to be able to use .htacces files and set mysql databases to names I choose (not like they are in ispconfig 2)
 
3) It would be nice to have the directory structured just like on the real linux server I use which puts sites in /home/sitename/public_html this has cpanel and whm which I understand may not be freely available.
 
The story so far... I already have isp ispconfig 2 on a Fedora 10 machine and am replacing that. I tried ispconfig 3 on this ubuntu setup but had some problems and couldn't find any useful documentation so abandoned it. Found the perfect server ispconfig 2 setup then realised that LTS is command line only I like to have a gui.
 
That's about it, thank you for reading my 1st post !

---

### Post by cmnorton on 2009-05-02
Start here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Cheesemill on 2009-05-02
> **greentrees said:**
> 
I'm looking to add a home web server to my shiny new 3rd time install of ubuntu 8.04 (not LTS).


> **greentrees said:**
> Hi All,
then realised that LTS is command line only I like to have a gui


LTS isn't command line only, all versions of Ubuntu 8.04 are LTS.
It's the Server version of Ubuntu that is command line only (although it is possible to install a GUI on it).

I don't run a WebUI on my LAMP server for administrating websites so I'll let someone else answer that one!
As for installing  Apache, MySQL and PHP, you can do the whole lot in one go by typing the following into a terminal:
```
sudo apt-get update && sudo apt-get -y install lamp-server^
```

For MySQL, I just install the MySQL GUI tools (MySQL Administrator and MySQL Query Browser) on my desktop machine, they're in the repos or available from [www.mysql.com]("http://www.mysql.com") for Windows.

This will let you create and administrate databases of any name you choose, although you may have to add a MySQL user with remote access privileges (or add remote access to the root account if security isn't an issue).

Cheesemill

---

### Post by cariboo on 2009-05-02
If you add the server name/ip address to your Windows computer's host file you won't need dns. 

If you have a network of over 10 computers, you may want to look at dnsmasq for name services. Dnsmasq is in the repositories.

---

### Post by greentrees on 2009-05-03
Many thanks chaps.

This all seems so much easier with ubuntu rather than fedora, the info in these forums is fantastic so spurred on by my new found confidence I've gone for virtualmin.  A single script install did pretty much everything I wanted.  It all seems far better than ispconfig I have setup multiple sites with ease and since added support for curl, gd and phpmyadmin all problem free so far.  I have a problem with ssl right now but that doesn't bother me too much as I need to learn more about that anyway.

---

### Post by Iowan on 2009-05-03
> **greentrees said:**
>  I have a problem with ssl right now but that doesn't bother me too much as I need to learn more about that anyway.
A couple of places to check: [https://help.ubuntu.com/community/forum/server/apache2/SSL]("https://help.ubuntu.com/community/forum/server/apache2/SSL")
[https://help.ubuntu.com/community/OpenSSL]("https://help.ubuntu.com/community/OpenSSL")

---

### Post by Francewhoa on 2009-06-29
I wrote a how-to handbook at [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)
It covers installing Virtualmin, Webmin & Usermin.

---

