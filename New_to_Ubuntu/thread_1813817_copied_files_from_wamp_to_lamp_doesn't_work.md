---
title: "copied files from wamp to lamp doesn't work"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by psychowants2bgeek on 2011-07-28
[SIZE=3]Hi,

I am new to ubuntu and have installed 11.04 successfully yesterday. Since then I installed LAMP and phpmyadmin with the guidelines from forum and have given all the rwx permission to the /var/www/* folders where I have my projects. I have been working with WAMP for quiet a while but bit confused with LAMP.

my problem is: I copied files from WAMP's www and pasted directly to LAMP's var/www/, now when I create new project/files inside var/www it works perfectly and easily executed using any browser, but I cannot run my old projects. I tried using both browsers and the results are:

Firefox: 
doesn't display anything, just blank page
error console: nothing
page info: connection not encrypted 

Chromium: [/SIZE]
[SIZE=1][COLOR=#000000][FONT=Times New Roman][FONT=Helvetica]**Server error**

The website encountered an error while retrieving **[http://localhost/test_site/index.php](http://localhost/test_site/index.php)**. It may be down for maintenance or configured incorrectly.
**Here are some suggestions:**


[LIST]
[*][Reload]("http://localhost/autoraft_skinned/index.php") this web page later.
[/LIST]

[COLOR=#777777]HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfill the request.


[/COLOR]
[/FONT][/FONT][/COLOR][/SIZE][SIZE=3]I'd really seeking the help [/SIZE]

---

### Post by lykwydchykyn on 2011-07-28
You need to check /var/log/apache2/error.log.

That's where server errors are going to be logged.

If you're not sure what to make of them, post the log here.

---

### Post by doas777 on 2011-07-28
within \var\www\<an old project>\ 
what is the output of 
```
ls -al
```

---

### Post by psychowants2bgeek on 2011-07-28
Hi guys,

thanks for prompt reply, one thing I learned today is not to jump on ubuntu and start humping by pasting codes in terminal... I am reading the basics now for the ease, I guess its better then to search for some particular thing whole day.

The main problem with my project was permissions issue, as lykwydchykyn said I checked the error log inside apache, and there were errors from yesterday.

When I did as doas777 said, it all opened my eyes.... 

as I read in some guidelines I initially typed $ chmod a+x -R /var/ww/* in terminal to grant all permission to the folders inside www, but I didn't check the files and their permissions, now when doas777 said to type /var/www/project ls -al the output was:

drwxrwxrwx 15 psycho psycho    4096 2011-07-28 18:56 .
drwxr-xr-x 24 psycho root     4096 2011-07-27 21:34 ..
drwx------  5 psycho psycho    4096 2011-07-26 22:58 admin
drwx------  2 psycho psycho    4096 2011-07-26 22:58 chatApplication
drwx------  4 psycho psycho    4096 2011-07-26 22:58 client
drwx------  2 psycho psycho    4096 2011-07-26 22:58 conf
drwx------  2 psycho psycho    4096 2011-07-26 22:58 css
-rw-------  1 psycho psycho 1660707 2008-05-26 09:39 db_automobiles.sql
drwx------  3 psycho psycho    4096 2011-07-26 22:58 editor
-rw-------  1 psycho psycho   16948 2008-03-23 19:35 favicon1.gif
drwx------  2 psycho psycho    4096 2011-07-26 22:58 graphs
drwx------  6 psycho psycho    4096 2011-07-26 22:58 images
drwx------  2 psycho psycho    4096 2011-07-26 22:58 includes
-rw-------  1 psycho psycho      46 2011-04-30 11:39 index.css
-rw-------  1 psycho psycho    2517 2011-07-28 18:56 index.php
drwx------  2 psycho psycho    4096 2011-07-26 22:58 scripts
drwx------  2 psycho psycho    4096 2011-07-26 22:58 styles
-rw-------  1 psycho psycho    5632 2008-05-14 21:23 Thumbs.db
drwx------  2 psycho psycho    4096 2011-07-26 22:58 videos
drwx------  2 psycho psycho    4096 2011-07-26 22:58 webalizer

after wards I typed the code: $ chmod -R 755 /var/www/* then it changed the permission. The output of ls -al now is:

drwxr-xr-x 15 psycho psycho    4096 2011-07-28 18:56 .
drwxr-xr-x 24 psycho root     4096 2011-07-27 21:34 ..
drwxr-xr-x  5 psycho psycho    4096 2011-07-26 22:58 admin
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 chatApplication
drwxr-xr-x  4 psycho psycho    4096 2011-07-26 22:58 client
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 conf
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 css
-rwxr-xr-x  1 psycho psycho 1660707 2008-05-26 09:39 db_automobiles.sql
drwxr-xr-x  3 psycho psycho    4096 2011-07-26 22:58 editor
-rwxr-xr-x  1 psycho psycho   16948 2008-03-23 19:35 favicon1.gif
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 graphs
drwxr-xr-x  6 psycho psycho    4096 2011-07-26 22:58 images
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 includes
-rwxr-xr-x  1 psycho psycho      46 2011-04-30 11:39 index.css
-rwxr-xr-x  1 psycho psycho    2517 2011-07-28 18:56 index.php
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 scripts
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 styles
-rwxr-xr-x  1 psycho psycho    5632 2008-05-14 21:23 Thumbs.db
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 videos
drwxr-xr-x  2 psycho psycho    4096 2011-07-26 22:58 webalizer


Now I am able to run the projects... thanks you guys !!!

---

