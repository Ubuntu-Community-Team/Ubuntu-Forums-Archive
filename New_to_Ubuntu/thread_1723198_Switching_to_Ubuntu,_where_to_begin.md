---
title: "Switching to Ubuntu, where to begin?"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by AmyLane on 2011-04-06
Hi, I have a server with windows 2008 standard installed along with plesk 8, I would like to move to linux because there is so much work involved trying to keep microsoft windows and plesk up to date, plesk seems easy to exploit and their support is not professional, what I need as a systems manager is to be able to swipe clean my server (all files have been backed up), once I install Ubuntu Server, I need a way to install Apache + PHP + mysql but also I need a way to setup virtual hosts at, [http://myserver/myclient1](http://myserver/myclient1), myclient2 and so on, my clients need to have sftp access into their folders but that directory needs to be locked/jailed so he/she can't get access to other files on the server and other clients by installing a php script to show all files on my server.  Sorry for a long post.  I've been using Ubuntu Desktop for 5 months now and I love it :)  Thank You, Amy.

---

### Post by lisati on 2011-04-06
I have vsftpd installed on my server to manage the ftp side of things, and have it set to limit users' access to their home directory: how to do this is explained in the [vsftpd tutorial]("https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html").

---

### Post by jmszr on 2011-04-06
AmyLane,

This may be of use to you: [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html) .

Also, here is a link to the server subforum: [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339) . Any server questions you may have will probably get a faster answer there.

---

