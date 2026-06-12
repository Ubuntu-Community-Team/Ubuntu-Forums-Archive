---
title: "I'd like to install a web server"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by bobmac on 2010-02-06
Folks,

I have ubuntu v8.04 LTS (desktop) with all the latest updates installed and also KDE 3

I'd like to install a web server (presumably Apache)

Do I need to install the v8.04 server version of ubuntu?

Can I install Apache without having to do heaps of command line linux stuff (of which I haven't a clue)?

Is there a tutor or some instructions that I can use that explains things in words of 1 sylable for non gurus?

How much memory does it take up. (I would like to put it on my laptop first to see how much of a mess I can make before loading it on my main machine)?

Any information will be gratefully received

regards,

Bob

---

### Post by rampageoberon on 2010-02-06
hello,

Apache is a good option, as is lighttpd. Perhaps the two links below will best help you.

But basically you can also isntall from the package manager (you don't need to install the server edition).

[http://myy.helia.fi/~karte/install_apache_on_ubuntu.html](http://myy.helia.fi/~karte/install_apache_on_ubuntu.html)
[http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html](http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html)

Hope this helps

---

### Post by mushwars on 2010-02-06
you are probably going to want an ftp server as well, I personally love vsftpd though it is a little hard to configure it is VERY easy to set up new users ( you dont have to create a .conf file for EVERY user ) 

Along with your webserver you are going to need PHP at least. You might also want perl and python (but you dont need them)


You might also want to install mysql. It is an opensource free database, and also get phpmyadmin to go along with that. 

I read a guide on how to make an ubuntu server, I will post the link when I find it, it is very insightful.


**never JUST install apache**

---

### Post by mushwars on 2010-02-06
just what the doc ordered.

[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)

I know its for 8.04 but there is a release for each one of those packages in the new repositories.

---

### Post by bobmac on 2010-02-06
rampageoberon,

Many thanks for your reply. The links look great.

On another front, I notice that with most of the chit chat about the Apache web server there is lots of talk abut mysql, php and so on. Do I need to install these at the same time? or do I need them? or can they be installed at any time.

As you'll probably have surmised by now I tend to do a bit of research on things then go ahead and try them out. Which is probably why I'm becoming an expert at reinstalling ubuntu as I invariably get into trouble and as I'm no guru I haven't a clue on how to back out of things.

Thanks again for your quick reply

regards,

Bob

---

### Post by Gadgetech on 2010-02-06
I use a LAMP setup on my netbook. It runs just fine on a 1.6GHz Atom and 1 GB of RAM. You can install it on Ubuntu desktop with:
```
sudo apt-get install lamp-server^
```

I have a full write-up with screen shots on my blog @ [http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)

The procedure for 8.04 is the same.

---

