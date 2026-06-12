---
title: "So I just insalled LAMP... Now what?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by diablo75 on 2009-11-07
I just setup LAMP on my Ubuntu server at home, but really don't know what to do from here.  Typing in "localhost" in the address bar in Firefox brings up the default It works!! web page, but I don't know exactly where this page is located locally.

What I want to do right off the bat is host a web page that asks the user to enter a username and password, granting them access to the rest of the site.  The intention is to use the server to share files with select friends and family.  How might this be done?

---

### Post by Ant59 on 2009-11-07
You should search Google for your answer. This forum is for Ubuntu, not web development.

If you want to change the page however, you need to delete the contents of the htdocs directory and write your own index.php

This will be the first page you see, when typing localhost. You can use PHP and MySQL to create a user-base and enable login via a form.

---

### Post by Paqman on 2009-11-07
If you just want to share some files it might have just been easier to set the machine up as an FTP server, instead of a web server.

I believe proftpd is highly recommended, but i've not used it myself.

---

### Post by Hospadar on 2009-11-07
The default web root on ubuntu is /var/www

I would second the ftp server for filesharing, also you might consider ssh on a second account, it's extremely secure, and with an ftp/sftp client like filezilla, it's very easy for anyone to connect (I have my lay friends connecting to my machine to grab pictures and whatnot all the time).

That said, it's totally do-able to use the webserver as well, especially if you want to host a photo gallery, etc.  Just google, there are about a billion guides to setting up the web server in any configuration that you want.

---

### Post by mörgæs on 2009-11-07
Maybe Opera Unite is an option:

[http://en.wikipedia.org/wiki/Opera_(web_browser)#Opera_Unite](http://en.wikipedia.org/wiki/Opera_(web_browser)#Opera_Unite)

---

### Post by Iowan on 2009-11-07
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a help page for LAMP... though it seems to be in the process of change.

---

