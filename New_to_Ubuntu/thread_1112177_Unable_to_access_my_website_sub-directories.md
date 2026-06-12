---
title: "Unable to access my website sub-directories"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by larz1st on 2009-03-31
I am running Ubuntu 8.10 server and have setup a website
/var/www/...

When I browse to the site, I can see the front page.  At the bottom
is a link to another directory- located still within www

However, clicking on it or entering the link into the address bar, I receive a FORBIDDEN You don't have permission to access /Link/ on this server.

My first thoughts were I need to change the permissions on the directory and/or the files within it.

Typed... chmod -R 7777 Link and when done, did a ls -l and got this back.

drwsrwsrwt 8  UserNameHere root ....

So.  I am confused.  What am I doing wrong?  (note: admitting my ignorance in advance. :(

Thanks!

Larry

---

### Post by blueridgedog on 2009-03-31
I do not have a server working at the moment (my life seems to be blessed in that I no longer have to babysit boxes).  However, the error is most likely caused by your apache config in that it is not allowing recursion.  Others with a server background may give you more exact pointers.  Also, debuging apache is aided by glancing at the log file after you get an error, by using the "tail" command on the log file (from memory, /var/log/httpd.error - but that may have changed).

---

### Post by kellemes on 2009-04-01
It's not "7777", it is "777", and that's not advisable since it'll give **everyone** permissions to read/execute/write.
```
chmod 755 filename/dir
```
So everyone can read/execute and only owner can also write.

---

