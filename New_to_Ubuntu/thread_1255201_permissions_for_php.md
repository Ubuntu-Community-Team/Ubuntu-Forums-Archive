---
title: "permissions for php"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by anatak on 2009-09-01
Hello,

I have a php script that has to write (fopen() and fwrite()) to files in my web directory.
The folder that holds the files is on my Desktop and is avaiklable via the apache settings.
See this guide if you would like to know how
[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

the problem is now that php can not write to the folder / files since it does not have permission.
I am trying to find out what process / user / daemon or anything similar is used by php to write to files and how to give permissions to that process

any helps or handy guides that you want to share ?
thanks in advance
anatak

---

### Post by ponto18 on 2009-09-02
I think the user you're looking for is "www-data".

Go to the "top" program to watch processes and press 'u' to select user and then enter "www-data" and you'll see all processes for that user.

Tell me if it worked.

---

### Post by anatak on 2009-09-02
Thank you ponto18,

I gave my folder 777 permissions and looked at the owner of the newly created files. Not the most elegant solution.

Didn't know the top program thanks for pointing that out to me.

now to the second part.
How do I give permissions to a process/user to write in a folder since I don't want to keep the 777 permissions.
I have been looking at the gui but could not readily found it.

Or do I have to use the terminal with 
chown -R username /foldername/   ?

kind regards
anatak

---

### Post by falconindy on 2009-09-02
'www-data' is the user who executes apache (and php) processes. You're correct in the idea that you need to chown the path to www-data. You can then peel the permissions back to 744.

---

