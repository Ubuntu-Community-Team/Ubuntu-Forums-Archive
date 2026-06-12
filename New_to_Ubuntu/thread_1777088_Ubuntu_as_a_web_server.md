---
title: "Ubuntu as a web server"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-07
Im getting a reasonably speced optiplex soon. I wish to use it as a web server with php and mysql. Can I just use my ubuntu install disk or do I have to download ubuntu lts ?

---

### Post by HermanAB on 2011-06-07
As always, it depends...

If you are going to maintain the server yourself, then you can use the latest version of buntu and have fun.

If you intend that some hired help will maintain it, use LTS Server and get a Canonical support plan.

If you intend to rent a dedicated server from a server farm, then you should use whatever they provide - usually Red Hat.

---

### Post by kalimojo on 2011-06-07
Im running it at home myself. What is the main difference between 11.04 and LTS ? Will 11.04 run php,mysql etc ? Does LTS have a GUI ? Can I run virtualbox on LTS ?

---

### Post by Paqman on 2011-06-07
> **kalimojo said:**
> Im running it at home myself. What is the main difference between 11.04 and LTS ?

11.04 has newer packages than 10.04, but isn't supported for as long, so you'd have to upgrade sooner. If you want a super stable server that you don't have to fiddle about with, go with the LTS.

>  Will 11.04 run php,mysql etc ?

Yes, all versions of Ubuntu can run a LAMP stack.

>  Does LTS have a GUI ?

All versions of Ubuntu are available as either a desktop or server. The server version does not have a GUI. But you could install server packages on the desktop and vice versa. Most people run their servers without a GUI to save resources, but you can install something like [Webmin]("http://www.webmin.com/") to make life a little bit easier.

> Can I run virtualbox on LTS ?

Of course.

---

### Post by kalimojo on 2011-06-07
Ok. I think ill run 11.04 with lamp. I would like a GUI and virtualbox. Im looking at a book called ubuntu 10.04 LTS server by ubuntu.

---

### Post by collisionystm on 2011-06-07
> **kalimojo said:**
> Ok. I think ill run 11.04 with lamp. I would like a GUI and virtualbox. Im looking at a book called ubuntu 10.04 LTS server by ubuntu.


Just install Zentyal. [www.zentyal.com](www.zentyal.com)

based on 10.04 server and can be a web server. Very easy to setup.

---

### Post by Paqman on 2011-06-07
> **kalimojo said:**
> Ok. I think ill run 11.04 with lamp. I would like a GUI and virtualbox. Im looking at a book called ubuntu 10.04 LTS server by ubuntu.

Well, you have two options:
[LIST=1]
[*]Install Ubuntu server and add the desktop packages to give you a GUI
[*]Install Ubuntu desktop and add the server packages to give you your web server
[/LIST]

Let us know which way you decide to go and we can tell you what packages to install.

---

### Post by cavh on 2011-06-07
The easiest way to install a LAMP stack is using these commands from a terminal prompt (Application -> Accessories -> Terminal):

(1) check whether the tasksel package is installed:
```
whereis tasksel
```

If it is found, go to (4). If it is not found, go to (2)

(2) update your repository lists:
```
sudo apt-get update
```
(insert your usual password)

(3) install tasksel:
```
sudo apt-get install tasksel
```

(4) run tasksel:
```
sudo tasksel
```

When the tasksel screen comes, use your arrow keys to move up and down the list and your spacebar to select or deselect an entry. Select the LAMP option. DO NOT DESELECT ANY OTHER OPTION! Use your tab key to get to the OK link, and the Enter key as normal. Then follow the tasksel prompts to install the LAMP stack.

---

### Post by kalimojo on 2011-06-07
> **Paqman said:**
> Well, you have two options:
[LIST=1]
[*]Install Ubuntu server and add the desktop packages to give you a GUI
[*]Install Ubuntu desktop and add the server packages to give you your web server
[/LIST]

Let us know which way you decide to go and we can tell you what packages to install.

ok, im testing on my laptop just now which has 11.04 

I found the following instructions online

++++++++++++++++++++++++++++++++++++++++++++++++
I’ll be explaining how to install **LAMP stack** with **PHP 5.3.6** without **compiling**
 It’s fairly easy using the dotdeb repository
 first we need to add the **dotdeb** application sources to our sources list
 [?]("http://www.omaroid.com/installing-lamp-with-php-5-3-6-on-ubuntu-11-04-natty-narwhal/#")
1
sudo nano /etc/apt/sources.list



 And copy and paste the following lines and save using ctrl+o
 [?]("http://www.omaroid.com/installing-lamp-with-php-5-3-6-on-ubuntu-11-04-natty-narwhal/#")
1
2
3
4
5
deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
deb-src [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
 
deb [http://php53.dotdeb.org](http://php53.dotdeb.org) stable all
deb-src [http://php53.dotdeb.org](http://php53.dotdeb.org) stable all



 
 Then we’ll add the GPG key for the dot deb repository by the following command:
 [?]("http://www.omaroid.com/installing-lamp-with-php-5-3-6-on-ubuntu-11-04-natty-narwhal/#")
1
wget [http://www.dotdeb.org/dotdeb.gpg](http://www.dotdeb.org/dotdeb.gpg) && cat dotdeb.gpg | sudo apt-key add -



 Now we’ll refresh the packages list by the following command:
 [?]("http://www.omaroid.com/installing-lamp-with-php-5-3-6-on-ubuntu-11-04-natty-narwhal/#")
1
sudo apt-get update



 Now we’re ready to install our **LAMP stack**
 [?]("http://www.omaroid.com/installing-lamp-with-php-5-3-6-on-ubuntu-11-04-natty-narwhal/#")
1
sudo aptitude install apache2  apache2-mpm-prefork mysql-client-5.1 mysql-server-5.1 php5 php5-cli  php5-mysql libapache2-mod-php5 php5-mcrypt php5-curl php5-gd phpmyadmin



 Now we’re all set, just need to test it
go to [http://localhost/](http://localhost/) to test apache
and we can test php by writing in the bash
 [?]("http://www.omaroid.com/installing-lamp-with-php-5-3-6-on-ubuntu-11-04-natty-narwhal/#")
1
php -v



 you should see
 [?]("http://www.omaroid.com/installing-lamp-with-php-5-3-6-on-ubuntu-11-04-natty-narwhal/#")
1
2
3
4
PHP 5.3.6 with Suhosin-Patch (cli) (built: May 20 2011 14:17:04) 
 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologie


++++++++++++++++++++++++++++++++++++++++++++++++++++++++++=

i created a helloworld.php file in /var/www and ran [http://localhost/helloworld.php](http://localhost/helloworld.php) 
and it worked ok.

So when I get my Optiplex I will install 11.04 and then install the server packages to set up a web server. I dont expect much traffic on the web server so I will be needing the GUI to run virtualbox so I can try out stuff.

Im really doing it as an exercise and to learn.

---

### Post by mastablasta on 2011-06-07
quite complicated. you could just instal tasksel ([https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)). and then just select the things you want and it will install it. for example select LAMP and go.

---

### Post by kalimojo on 2011-06-07
Thanks all. I will be using tasksel on the server.

---

### Post by kalimojo on 2011-06-07
Thanks all. I will be using tasksel on the server.

---

### Post by Paqman on 2011-06-07
Those instructions you posted were trying to get you to add a third-party source and get your packages from there. That's never a particularly good idea if the packages you want are available in the Ubuntu repos anyway. The official repos should always be the place to go to for software, especially on a web server that could be facing the internet. It's good to be paranoid about security on servers, as they're prime targets.

---

### Post by kalimojo on 2011-06-07
> **Paqman said:**
> Those instructions you posted were trying to get you to add a third-party source and get your packages from there. That's never a particularly good idea if the packages you want are available in the Ubuntu repos anyway. The official repos should always be the place to go to for software, especially on a web server that could be facing the internet. It's good to be paranoid about security on servers, as they're prime targets.

Thanks again. I will use tasksel on the server.

---

### Post by robertmf on 2011-06-23
Thanks for the tasksel headsup :)

---

