---
title: "allow ftp to /var/www"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-03-24
i have managed to setup apache, php and mysql on my ubuntu desktop and all is running smoothly and people can access my site which isnt really much of a site. i want to setup ftp so i can edit the site whenever. the site is setup in the default apache location /var/www if that helps. (not in a subdirectory like i saw recommended somwhere eg var/www/index.php)

people are probably going to think im advertising or somthing but could you please visit [www.pspunleashed.co.cc](www.pspunleashed.co.cc) and tell me how long my site take to load as i am running the server over wifi until i move the computer next to the router , thanks sam.

---

### Post by jbrown96 on 2009-03-24
It didn't seem to take an appreciable amount of time to load. Very fast

---

### Post by freak42 on 2009-03-24
fyi: if you are running your server on a regular user internet connection then wifi probably isn't your limiting speed factor in serving pages.

(it works btw)

hth

---

### Post by Gen2ly on 2009-03-24
ftp probably isn't the best thought as it sends passwords in clear text.  Best to use sftp.  Here's a [bit]("http://ubuntuforums.org/showthread.php?t=747697") about it.

---

### Post by pspsampsp on 2009-03-24
ok so i installed openssh what do i do now?

---

### Post by mcla0203 on 2009-03-24
type in "ssh localhost" on your computer and if it works you can use scp to login to that machine

---

### Post by mcla0203 on 2009-03-24
sorry, type that in the terminal of course.

---

### Post by pspsampsp on 2009-03-24
lol i knew to type it into terminal , can i change the default directory that ssh goes to?

---

### Post by thehouseofho on 2009-03-24
sFTP is just a protocol for transferring files.  Instead of using FTP to upload files you would use sFTP.

In order to change the home directory of the FTP account, you can edit the passwd file located in /etc.  Look for the name of the FTP account and look for something that looks like:

/home/user:/[location of user's FTP folder]

Type the location of where you would like the home directory (in your case /var/www) after the colon.

---

### Post by pspsampsp on 2009-03-24
ok ive changed that but now what would i put in an ftp client like filezilla as the sftp user?

sorry about this ive never used sftp/ssh

---

### Post by thehouseofho on 2009-03-24
> **thehouseofho said:**
> sFTP is just a protocol for transferring files.  Instead of using FTP to upload files you would use sFTP.

In order to change the home directory of the FTP account, you can edit the passwd file located in /etc.  Look for the name of the FTP account and look for something that looks like:

/home/user:/[location of user's FTP folder]

Type the location of where you would like the home directory (in your case /var/www) after the colon.

Sorry, a mistake on my part.  You would need to change the passwd file within Apache, not the one located in /etc.

---

### Post by thehouseofho on 2009-03-24
> **pspsampsp said:**
> ok ive changed that but now what would i put in an ftp client like filezilla as the sftp user?

sorry about this ive never used sftp/ssh

The username is the same as an FTP account, all you're doing is using a different protocol to connect to the server.

---

