---
title: "Problem with Apache, MySQL, Php"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by Solyomszem on 2007-03-06
Hi!

At first I have to let everybody know that I am a noob...
I wanted to "build" an environment where I can toy with Joomla! (A CMD system). I've installed apache2, mysql5, php5.
 The first problem occured when dpkg tried to configure mysql-server-5.0. It could not start the service. Later on I've found out (with the help of forums) that some has to disable the innoDB service at /etc/mysql/my.cnf. So I did (skip-innoDB). Nothing happened. After I found out that I have problems with the localhost. So I did skipped that line too in mx.cnf. (Where it defined to check it.) I moved on to install apache.
 Apache could not find localhost. Nor can I with ping or any other tool I know. What can be the problem?

 I am using a notebook with wifi enabled. (I could manage it only by deleting a file configuring my connections. This way it is able to find my wireless network. (This file is created by the graphical app in administration/networking.))

 Any suggestions or help will be appreciated!!!

---

