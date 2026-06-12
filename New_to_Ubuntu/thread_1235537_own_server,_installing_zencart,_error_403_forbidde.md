---
title: "own server, installing zencart, error 403 forbidden access"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Adam65 on 2009-08-09
Hi, I am new to Ubuntu and this is my very first post.

I have finished customising a zen cart on a winxp development machine and now it's time to migrate the finished product onto my in house ubuntu web server.

I have copied all of the files to my /var/www/ folder.
The next step is to install zencart on the linux machine so I type into a browser:
[http://localhost/zen/zc_install](http://localhost/zen/zc_install)

Normally this would start the file index.php in the zc_install folder (as it does in windows) but I get this message instead:

403 Forbidden
**Forbidden**

 You don't have permission to access /zen/zc_install on this server.


Now, I understand that, most probably, permissions are to blame... but I have tried going directly to that file (and directory) and changing the permissions (right click, properties, permissions, setting every section to read and write) but that seems not to be working.


I can access phpmyadmin so I know php is installed properly, I have been able to create databases in mysql and tested apache ok (apache message "It Works" calls up the file index.html at /var/www/ no problem). I can't seem to work out how to get past this error 403. Can anyone please help?


Here is a copy of my ls -l /var :

total 52
drwxr-xr-x  2 root root  4096 2009-08-09 07:48 backups
drwxr-xr-x 17 root root  4096 2009-08-09 17:31 cache
drwxr-xr-x  2 root root  4096 2009-03-27 19:42 crash
drwxr-xr-x  2 root root  4096 2009-08-08 15:32 games
drwxr-xr-x 56 root root  4096 2009-08-09 17:31 lib
drwxrwsr-x  2 root staff 4096 2009-04-13 19:33 local
drwxrwxrwt  3 root root    80 2009-08-09 18:47 lock
drwxr-xr-x 17 root root  4096 2009-08-09 18:47 log
drwxrwsr-x  2 root mail  4096 2009-08-08 14:07 mail
drwxr-xr-x  2 root root  4096 2009-08-08 14:07 opt
drwxr-xr-x 18 root root   740 2009-08-09 21:30 run
drwxr-xr-x  6 root root  4096 2009-08-08 15:22 spool
drwxrwxrwt  2 root root  4096 2009-08-09 20:48 tmp
drwx------  2 root bin   4096 2009-08-08 15:45 webmin
drwxr-xr-x  3 root root  4096 2009-08-09 18:31 www


I would post an error log too but I am so new to all of this I don't know which error log to look in!!


I have read alot of post's with no success.



I would be extremely grateful if someone could assist me.


Thank you in advance for any suggestions you might have.

---

### Post by Adam65 on 2009-08-09
Hi, is anybody out there?

I am sorry if my question seems silly but I am very new to Ubuntu and had hoped to get just a little assistance.

I thought maybe nobody answered my post because you thought that the question was so dumb that it didn't warrant an answer.

Well I have been searching the forums and I have tried another couple of things:

I found out that Apache uses the user www-data so I went to the files and folders associated with my zencart and changed the permissions for that user, made wwwdata the owner and gave all the privileges I could but still I cannot get the index.php in the /var/www/zen/zc_install/ folder to initiate.

So you see it is not like I haven't tried multiple things or read multiple posts... I have... now I please really need some help.

Could someone direct me to a post or help in some way??

Please
Thank you

---

### Post by Adam65 on 2009-08-10
Please remove this entirely useless thread.

I had corrupt files in my zencart directory.

---

