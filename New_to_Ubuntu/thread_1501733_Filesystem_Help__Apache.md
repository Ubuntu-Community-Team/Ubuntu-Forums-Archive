---
title: "Filesystem Help / Apache"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by UserBrandon on 2010-06-04
I'm trying to install Apache's httpd webserver.  I've downloaded the .tar.gz , I have already run these commands:

```
gunzip -d httpd.2.2.15.tar.gz
tar xvf httpd.2.2.15.tar
```This leaves me with httpd.2.2.15 as a directory with all the Apache files.  This directory is in my downloads folder.  I have 2 main questions.  First, I am quite new to Linux, so what part of the filesystem am I going to want to install this to?  Second, how do I change where it installs to?  I've read something about a prefix= option, but how would I find/change this?

Thanks for any advice.

---

### Post by echo.whoami on 2010-06-04
why don't you install apache2 from synaptic???

maybe this will help you:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by UserBrandon on 2010-06-05
Thanks for the idea, but I could not find the personal feel I wanted about how and where to install each file.  I did however find out what I needed to do, and will post that here.

So starting from the beginning:

Download the httpd-VERSION.tar.gz from [Apache]("http://httpd.apache.org/download.cgi").
Open terminal, navigate to the directory containing the .tar.gz file and run the following:```
gunzip -d httpd-VERSION.tar.gz
tar -xvf httpd-VERSION.tar
```This will decompress the .gz file, and then extract the files from the .tar file.  After both commands you will be left with the same .tar file and a new directory file named httpd-VERSION.  Change your working directory to inside this new directory.

The next thing you will be doing is configuring apache before installation.  The simplest way to do this is to run ./configure, but most people will want to specify where apache will be installed (this is the problem I ran into).  The --prefix= tag allows you to specify this path, and there are also additional modules that you can enable or disable using tags on this command.  I am not going to pretend that I know what their impacts are, so I left mine default.  Running this command will take a little time as the installer checks for items on your system.```
./configure --prefix=PREFIX
```(for the record I used --prefix=/usr/local/apache)

Now all that is left to do is to compile the binary files and install the binary files in your defined PREFIX location and other places in the system.```
make
make install
```Apache is installed, but not running.  To run Apache, run the following:```
PREFIX/bin/apachectl start
```You can check if this worked by opening a web browser and entering [http://localhost/](http://localhost/)  If you see a page with something like "It Works!", then your install was successful and you are ready to begin adding files to your PREFIX/htdocs/ directory.

---

