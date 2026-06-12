---
title: "Apache2 no permission to save files in /var/www/html"
date: 2020-06-27
forum: Networking &amp; Wireless
---

### Post by christian-franksson on 2020-06-27
As topic says. I have installed apache2 and it works and I see the index.html that says ”It works!” That file is located in /var/www/html. But I don’t have permission change any file in that folder? Why is it like this?

---

### Post by TheFu on 2020-06-27
> **christian-franksson said:**
> As topic says. I have installed apache2 and it works and I see the index.html that says &#8221;It works!&#8221; That file is located in /var/www/html. But I don&#8217;t have permission change any file in that folder? Why is it like this?

Security.  

File and directory permissions are the 1st line of security on all Unix-like OSes.  Get used to it. Learn how to manage it. Most importantly, learn how hackers can abuse tiny mistakes that are commonly made by people new to Unix when they get frustrated and don't setup the most secure permissions needed for the task.

In general, it is a bad idea to allow any web server to have write access to file locations served by that web server userid. Systems get hacked daily when that happens.

BTW, if you want actual commands, we need facts. In this case, those facts would be the userid running the process you want to have write access, the output from '**id**' for that userid, and the **ls -al **permissions on the directory where the access is desired. Please use code tags, if you choose to post that data so the columns line up correctly.

---

### Post by christian-franksson on 2020-06-30
Okey, I will try to give you some more information.

in /var Directory
```
christian@franksson:/var$ ls -al
total 60
drwxr-xr-x 15 root      root     4096 jun 27 14:47 .
drwxr-xr-x 20 root      root     4096 jun 19 13:06 ..
drwxr-xr-x  2 root      root     4096 jun 30 07:37 backups
drwxr-xr-x 19 root      root     4096 jun 27 14:47 cache
drwxrwsrwt  2 root      whoopsie 4096 apr 23 09:38 crash
drwxr-xr-x 68 root      root     4096 jun 24 18:14 lib
drwxrwsr-x  2 root      staff    4096 apr 15 13:09 local
lrwxrwxrwx  1 root      root        9 jun 19 13:05 lock -> /run/lock
drwxrwxr-x 15 root      syslog   4096 jun 30 00:00 log
drwxrwsr-x  2 root      mail     4096 apr 23 09:32 mail
drwxrwsrwt  2 root      whoopsie 4096 apr 23 09:38 metrics
drwxr-xr-x  2 root      root     4096 apr 23 09:32 opt
lrwxrwxrwx  1 root      root        4 jun 19 13:05 run -> /run
drwxr-xr-x 11 root      root     4096 jun 19 23:33 snap
drwxr-xr-x  8 root      root     4096 jun 24 18:14 spool
drwxrwxrwt 10 root      root     4096 jun 30 08:15 tmp
drwxr-sr-x  3 christian www-data 4096 jun 27 15:10 www
christian@franksson:/var$
```

And in /var/www

```
christian@franksson:/var/www$ ls -al
total 24
drwxr-sr-x  3 christian www-data  4096 jun 27 15:10 .
drwxr-xr-x 15 root      root      4096 jun 27 14:47 ..
drwxr-xr-x  2 root      root      4096 jun 27 14:48 html
-rw-r--r--  1 christian www-data 10926 jun 27 15:10 index.html
christian@franksson:/var/www$ 
```

And from my apache2.conf file 

```
<Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>

<Directory /usr/share>
        AllowOverride None
        Require all granted
</Directory>

<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

#<Directory /srv/>
#       Options Indexes FollowSymLinks
#       AllowOverride None
#       Require all granted
#</Directory>
```

One thing i found wierd is that the index.html file that is shown when you have successfully installed Apache is located in /var/www/html but in the apache2.conf file here above it says /var/www/

Im greatful for any help I can get here. 

Regards Christian.

---

### Post by TheFu on 2020-06-30
/var/www/html
```
dr_w_xr-xr-x  2 _root_      root      4096 jun 27 14:48 html
```
To place any files inside html, the root account is required because only root has write on that directory (which is actually a file).

What you have is a basic Unix permissions problem.  I've written how to learn permissions here a number of times - perhaps 20. There isn't any easy way. Learning about 90% takes less than 1 hour, but you have to be present AND active in the learning.

Unix is multi-user from the core to the top.  Users that need to work on the same files, that includes userids created just for processes to run (daemons), like www-data, often should be placed into a shared group to be able to modify the same files.

File and directory permissions are not automatically inherited from the parent directory without taking some extra steps. This is usually only setup for groups of real humans, not daemon files. There are exceptions.

Find a Unix permissions tutorial. Work through it. DO NOT JUST READ IT.  Open some terminals, create a *play area* in a temporary directory - some where under /tmp/foo/ would be good.  Type the commands from the tutorial yourself - should take about 15 minutes. Try some additional commands. When finished with that, you have about 20% of the knowledge, but it is just memorization at this point.  We want that _lightbulb moment_ to happen.  For that, open 3 terminals, create 3 user accounts and 3 groups. Mix and match the membership of those groups between the userids. Use the 'id' command to see that you have the correct mix where they all share 1 group, 2 share another group and the other 2 share the 3rd group.  Now using the 'touch' and 'mkdir' commands, create empty files and directories using the different userids and groups. You'll need to use 'chgrp'.  

Now, start creating directories with every possible permissions setup allowed.
700
750
755
775
777
771
751
711
and don't forget 111 and 000 permissions.   Which userids can modify the permissions of the directories? Does being in the group help?

Put files inside each of those directories. There are more permissions for files, so set some with the directory permissions above, but include some with these:
600
640
660
666
444
440
400
Add some text to each of the files. Mix and match groups for the different files.  Which userids can change the group on each file?

See which userids can 'cd' into the directories and which cannot. See which userids can 'view' files inside those directories and which cannot. See which userids can run programs and/or scripts inside those directories and which cannot. BTW, the answer is different for scripts than for compiled programs, so be certain to check that too. 
Now, see which userids can modify/edit the files in the directories and which can delete the files.

When you are done about 45 minutes later, Unix permissions aren't something you'll need to struggle with again, but you have to do the work and have that 'ah ha' moment, then spend 5 minutes validating that your belief about how things work is actually the truth.

How would you setup the permissions to allow all users, except 1 to view a file?  There are a few different answers.
Remember the permissions are split into 4 groups. Above, I've only showed 3 of the 4.
[LIST]
[*]owner
[*]group
[*]other
[/LIST]
are the main 3 groups.  'other' is sometimes called 'world', but that is incorrect. Why is that wrong?
At this point, you should have about 80% of the knowledge for permissions.

The last permissions group are the settings for setuid, setgid, marking as a directory and something called the 'sticky bit'. These are used just a few times a year, but are important for all sorts of security needs.  It won't hurt to skim over what they do, but only time and experience will teach the real meaning for each.  setgid is important when a group of users needs to work on the same files in the same directories.  setuid is something normal users don't ever touch and most admins have an awareness about, but don't usually setup.  You can read up about the sticky bit.  /tmp/ uses it, but I've never seen it used anywhere else that I can recall.

The apache2.conf file is an overview file. The sites-enabled/ directory has the specific settings for each virtual domain. The files in the sites-enabled/ directory are normally symlinks from the sites-available/ directory. This makes a nice work-area for configs that aren't ready to be live.

TL;DR

```
sudo chown christian:www-data  /var/www/html
```  This may or may not be a good idea. It depends on the type of files put inside.  If any php code goes inside, I'd be extremely cautious to ensure the www-data account doesn't have write permissions.

---

### Post by christian-franksson on 2020-06-30
Thank you for your help, I will go through this and leran it.

Regards Christian

---

