---
title: "Setting up ubuntu as a web server for LAN network?"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by panupat on 2010-11-03
I'm working with PHP, mySQL, using cms like joomla and the like. Currently I'm testing everything locally using appserv. But I'm thinking about setting up 1 PC to work as a central web server to test out my script/websites. The current set up is just a home network: 4 PCs connecting to the internet through 1 router-modem.

Can anyone help me get started? I'm completely new to linux/ubuntu. What are some of the configuration/software I will need to get this going? The ubuntu will only be used within our own LAN.

- to browse to the test server using [http://.](http://.).... ?
- ftp to upload file to it in addition to direct copying?

---

### Post by s3MA00RRNY on 2010-11-04
You'll want to install the CMS files to /var/www. Then run the CMS's install script (Follow the readme).

You might find CMS Made Simple easier. I certainly did for my first site. Just saying.

To set up the server, the easiest thing to do is to get a Ubuntu server disc (I would recommend 10.04 at this point) and select LAMP server option during install (plus whatever else you want). LAMP stands for Linux, Apache, MySQL, and PHP. That should get you up and running without too much fuss.

---

### Post by drdos2006 on 2010-11-04
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

