---
title: "help needed in installing apache"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by vinaykumarjg on 2011-06-09
Hello all,

  I had a problem with apache, which I used with php. It was showing some errors as "forbidden 403 ...". It was not loading images and css files that were stored in another folder, when accessed the page using localhost thing. I have a fresh copy of ubuntu installed now. I need some instructions on how to get apache installed with the problem solved of loading files from other folders. Please help! and thanks.


  vinay.

---

### Post by hakermania on 2011-06-09
This is what I've installed so as to run apache:
[IMG]http://img853.imageshack.us/img853/4908/screenshotzn.png[/IMG]
I didn't have any other problem, I placed files at /var/www/ and everything worked just fine

---

### Post by Paqman on 2011-06-09
> **vinaykumarjg said:**
> It was showing some errors as "forbidden 403 ...". It was not loading images and css files that were stored in another folder

Have you checked the permissions on the folders?

---

### Post by vinaykumarjg on 2011-06-09
yes I checked. It was as same as shown with some discussion forums.

---

### Post by hakermania on 2011-06-09
> **vinaykumarjg said:**
> yes I checked. It was as same as shown with some discussion forums.

Nice, did you tried to just install the packages I mentioned?

---

### Post by webofunni on 2011-06-09
Do 

ALT+F2-->gnome-terminal 

execute 

```

tail -f /var/log/apache2/error.log

```

access the page again and paste the o/P of above command here.

---

### Post by vinaykumarjg on 2011-06-09
Here's the output of the command

tail -f /var/log/apache2/error.log




vinay@linux-terminal:~$ tail -f /var/log/apache2/error.log
[Thu Jun 09 19:20:21 2011] [notice] caught SIGTERM, shutting down
[Thu Jun 09 19:20:28 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Thu Jun 09 19:20:35 2011] [notice] Graceful restart requested, doing restart
[Thu Jun 09 19:20:35 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Thu Jun 09 19:25:09 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Jun 09 19:25:12 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Jun 09 19:39:41 2011] [notice] caught SIGTERM, shutting down
[Thu Jun 09 19:39:42 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 09 19:49:37 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /var/www/001.jpg, referer: [http://localhost/index.html](http://localhost/index.html)
[Thu Jun 09 19:49:47 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /var/www/001.jpg, referer: [http://localhost/index.html](http://localhost/index.html)

---

### Post by vinaykumarjg on 2011-06-09
Yeah, I installed.

---

### Post by webofunni on 2011-06-09
what is the permission of the files ?

```

ls -l /var/www/
ls -ld /var/www

```

?

---

### Post by vinaykumarjg on 2011-06-09
> **webofunni said:**
> what is the permission of the files ?

```

ls -l /var/www/
ls -ld /var/www

```?

here's the output::::

 ls -l /var/www/
total 236
-rw------- 1 vinay vinay 230463 2006-11-23 13:40 001.jpg
-rw-r--r-- 1 root  root     111 2011-06-09 19:49 index.html
-rw-r--r-- 1 root  root      30 2011-06-09 19:37 test.php
vinay@linux-terminal:~$ ls -ld /var/www
drwxrwxrwx 2 root root 4096 2011-06-09 19:49 /var/www

---

### Post by webofunni on 2011-06-09
try 

```

chmod 644 /var/www/001.jpg

```

---

### Post by vinaykumarjg on 2011-06-09
anyone please help me on this.

---

### Post by vinaykumarjg on 2011-06-09
> **webofunni said:**
> try 

```

chmod 644 /var/www/001.jpg

```


its working!!!!!!!:p .[FONT=Microsoft Sans Serif]**thanks a lot**[/FONT].
 Am i needed to change the permission for each file i use? is there any other ways to do it at once?:confused:



vinay

---

### Post by webofunni on 2011-06-09
How you created that file ? That was under your username, so I guess you created it. not apache.

---

