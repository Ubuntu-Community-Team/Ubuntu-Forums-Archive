---
title: "Setting only one folder in /var/www/html to to 777 ?"
date: 2014-07-22
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2014-07-22
I'm testing a package written in php and all it needs installed on the web server is a folder in /var/www/html. For the sake of this question, let's call it test: /var/www/html/test is the new folder to be installed and filled with php goodness.

The only way I can get the application to run is with the entire contents of /var/www/html/test set to 777 permissions. 775 seems to work except when trying to do things like adding new users within the web-based GUI.

I've read dire warnings about using this permissions setting on /var/www but not on a specific folder within that folder. In other words, is the rest of the server safe from any shenanigans that may be going on within /var/www/html/test?

---

### Post by TheFu on 2014-07-22
php != goodness. This is just 1 opinion.

If any webapp requires more than an upload directory to have 777 (and that isn't needed either), I wouldn't use it. The programmer doesn't understand UNIX file/directory permissions and all their code is suspect of huge security flaws. After all, that is the key to UNIX system security.

You are correct in asking this question.  Heck - if "other" needs even read permissions, I don't think I'd use the program.  File access until webapps is owned by the userid running the webapp - so no "other" users need access at all unless there is some fifo or pipe used - then I'd expect the 2 userids to be in the same group.  Anything less is just lazy, IMHO.  This is one way that servers get hacked.

---

### Post by SeijiSensei on 2014-07-22
You can avoid granting rights to "others" by making the directory where the application is stored be owned by the www-data user that Apache runs as.  If /var/www/html/test is owned by someone other than www-data, then create a group for that directory owner and put the www-data user in that group.  Then you can use 770 permissions on directories and 660 permissions on files.  

My WordPress directory is owned by me and my group.  The Apache user also belongs to my group.

---

### Post by scottbomb on 2014-07-22
Thanks guys! Fortunately, I was able to find a guide for this particular application, outlining what files and folders should have what permissions. This is my first time hosting my own web server so it's been an interesting learning experience. I also changed the group from root to www-data. So far, it seems to be working well.

---

### Post by TheFu on 2014-07-22
You may want to read a few other threads here - servers ARE being hacked, so taking pro-active steps BEFORE is necessary.
I read yesterday a huge worm was going though many sites.  Be careful out there.

Oh ... and they aren't targeting you specifically (well, unless your site is high value), they (via bots) are targeting everyone.

---

