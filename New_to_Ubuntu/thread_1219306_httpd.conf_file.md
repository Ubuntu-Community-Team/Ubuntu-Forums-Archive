---
title: "httpd.conf file"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by elm_user on 2009-07-21
I edited the httpd.conf file and added the directive.
 
UserDir enabled U1T1
UserDir public_html 
 
before this entry, httpd.conf file was empty.
I then restarted apache using command
 
sudo /etc/inti.d/apache2 restart
 
I receive an error msg saying
 
syntax error on line 1 of /etc/apache2/httpd.conf:
invalid command 'UserDir', perhaps misspelled or defined by module not included in the server configuration
 
I'm trying to allow user U1T1 to publish content from the directory /home/U1T1/public_html. file name is index.html. How can I do this?

---

### Post by JohnnySage50307 on 2009-07-21
[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)
 
This link is a good howto on setting up user directories to allow individual websites.  I tried looking in my httpd.conf file to give you a good example of how I did it, but I can't seem to find where in it I wrote it.

---

### Post by elm_user on 2009-07-21
I understand those directions, but....
 
I don't understand how or where to create [www.example.com]("http://www.example.com") needed in the URL. 
 
the URL [http://example.com/~rbowen/file.html](http://example.com/~rbowen/file.html) will be translated to the file path /home/rbowen/public_html/file.

---

### Post by Wollongong on 2010-11-01
The error message "invalid command 'UserDir', perhaps misspelled or defined by module not included in the server configuration"
indicates that the userdir module is not being loaded.

This module is supposed to be "built in", whatever that means. 
With some version of Apache, it is loaded automatically even if there is no entry in /etc/apache2/mods-enabled/

However, with apache2 version 2.2.16-1ubuntu  (as in ubuntu 10.10 maverick),
it seems necessary to load userdir explicitly, which you do as follows:

$ cd /etc/apache2/mods-enabled
$ sudo ln -s ../mods-available/userdir.load .
$ sudo ln -s ../mods-available/userdir.conf .
$ sudo apache2ctl restart

---

