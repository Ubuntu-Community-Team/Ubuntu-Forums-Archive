---
title: "Set up for a computer lab"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by rchapman38654 on 2009-08-24
I am a public school teacher & I teach web page design.  I would like to set up a linux web server in which each student in the class can ftp their pages to the web server.  Any suggestions on the best way to get started - I've installed (then uninstalled) LAMP, an ftp package, wordpress, and several other "experiments".  What I would like to have is the following
1) a gui interface for the server
2) ftp access to the server for students
3) remote management
4) joomla & wordpress
 
Any suggestions on getting started will be greatly appreciated.

---

### Post by Augsburg on 2009-08-24
curlftpfs works well for a graphical ftp connection. It mounts an ftp folder as if it were a disk drive.

---

### Post by decoherence on 2009-08-24
> **rchapman38654 said:**
> I am a public school teacher & I teach web page design.  I would like to set up a linux web server in which each student in the class can ftp their pages to the web server.  Any suggestions on the best way to get started - I've installed (then uninstalled) LAMP, an ftp package, wordpress, and several other "experiments".  What I would like to have is the following
1) a gui interface for the server
2) ftp access to the server for students
3) remote management
4) joomla & wordpress
 
Any suggestions on getting started will be greatly appreciated.

If you have fairly recent hardware that supports virtualization, the simplest solution might be to find a virtual appliance that is already set up to do this. I've had very good luck with [JumpBox]("http://www.jumpbox.com") but there are others that are cheaper/free.

1) a gui interface for the server

JumpBoxes don't have a GUI per se, but they do give you a web-based graphical setup tool that covers things like network configuration, administrative access and backups (that's for the paid version.)

2) ftp access to the server for students

a word of advice... don't use FTP, particularly where there are student involved. The problem with FTP is that it sends your passwords over the network in clear text. That means, if you have a clever enough student, your password can be read.

instead, use SSH, which encrypts all traffic. FTP clients like Filezilla support doing file transfers over SSH as if it were FTP.

3) remote management

The web app (Joomla, for instance) is, of course, managed over the web. The (Jumpbox) administrative interface is also managed over the web. If you need more than that, there is ssh. You may also be interested in webmin.

4) joomla & wordpress

both available from Jumpbox.

Let me just stipulate that JumpBox is the one I use... there are many others, some free. Take a look at [VMWare's library]("http://www.vmware.com/appliances/"), noting that most of these will run on virtual machines other than VMWare.

---

### Post by superprash2003 on 2009-08-24
1)[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)
2)try gproftpd
3)remote desktop+ssh
4)just download them from the internet and install after installing LAMP

 do you want access to it over the internert or just within your network?

---

### Post by halitech on 2009-08-24
you will need a web server and an ftp server to start. 

I would use vsftpd for the ftp server and apache for the web.

vsftpd setup instructions
[http://www.debianhelp.co.uk/vsftpd.htm](http://www.debianhelp.co.uk/vsftpd.htm)

apache with Mysql and php5
[http://howtoforge.org/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.04-lamp](http://howtoforge.org/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.04-lamp)

For a GUI, use ebox
[http://ebox-platform.com/](http://ebox-platform.com/)

Joomla
[http://www.joomla.org/](http://www.joomla.org/)

wordpress
[http://wordpress.org/](http://wordpress.org/)

I'm not sure but I think you need to download and install ebox, joomla and wordpress from their websites

---

### Post by MrWES on 2009-08-24
> **rchapman38654 said:**
> I am a public school teacher & I teach web page design.  I would like to set up a linux web server in which each student in the class can ftp their pages to the web server.  Any suggestions on the best way to get started - I've installed (then uninstalled) LAMP, an ftp package, wordpress, and several other "experiments".  What I would like to have is the following
1) a gui interface for the server
2) ftp access to the server for students
3) remote management
4) joomla & wordpress
 
Any suggestions on getting started will be greatly appreciated.

This might help.

[http://www.theclassroomserverproject.org/]("http://www.theclassroomserverproject.org/")

---

### Post by rchapman38654 on 2009-08-25
Got ubuntu linux installed on yesterday as well as ubuntu-desktop & webmin. Will work on SSH, phpmyadmin, and setting up Apache on today. I have a virtual hosting account in which there is a public_ftp folder & a public_html folder - in the public_html folder are different folders for the different domains that I host. How would I configure Apache & SSH to have this kind of set up. I would like for each student to have a folder that they (& myself) will only have access to.
 
Thank you so much for you assistance.
 
R. Chapman
Whitehaven HS, Memphis, TN

---

### Post by rchapman38654 on 2009-08-25
just point apached to /home/public_html/ folder... will start working on creating student folders in this folder... :)

---

