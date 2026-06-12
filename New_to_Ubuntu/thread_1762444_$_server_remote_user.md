---
title: "$_server remote_user"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by BigSnooze on 2011-05-19
Hi

 Although this maybe a PHP issue it is the Linux component of it which i am stuck on, I hope you will bear with me while I explain.

 A new LAMP server has been built to replace an ageing system and the PHP code has been copied across. This was done by A.N.Other.
 We use Windows Active directory for user authentication to our Webpages.
 In the system we are trying to access the home page index.php opens automatically if the logged in user is a member of the relevant AD group. But this is not working.

 I have been asked to help because I have a small amount of PHP knowledge and the system admin thinks this is where the problem lies, my Linux knowledge consists of reading a dozen pages in a book and a couple of hours googling.

 The code uses the $_SERVER['REMOTE_USER'] variable to authenticate the logged in user. phpinfo() reveals that the $_SERVER['REMOTE_USER'] variable does not exist, although it does exist though on the server where the code originally comes from.
 My problem is how to install/enable the use of $_SERVER['REMOTE_USER'] on this newly built server.

_I have so far taken the following steps_:-
 Installed PEAR and LDAP on the Linux server.
 Tried to add the following line to my Apache2.conf file...
 LoadModule ntlm_winbind_module /usr/lib/apache2/modules/mod_auth_ntlm_winbind.so
 But when doing so the apache service will not restart.

 I have commented the line out for now and tried to add the module with -
 # autoconf
 ./configure
 apxs2 -DAPACHE2 -c -i mod_auth_ntlm_winbind.c
 but as soon as I hit autoconf it comes back with the error:
 autoconf error no input file.

 I have drawn a blank from there. In fact I might be heading in completely the wrong direction, I don't know. I need someone to hold my hand. I hope that I have given enough information and give thanks in advance for any help received.
 BigSnooze

---

### Post by ApOgEEs on 2011-05-26
Have you look into this manual?
[http://php.net/manual/en/features.http-auth.php](http://php.net/manual/en/features.http-auth.php)

---

### Post by jtarin on 2011-05-26
Might have better luck posting your question [here.]("http://ubuntuforums.org/forumdisplay.php?f=339")

---

