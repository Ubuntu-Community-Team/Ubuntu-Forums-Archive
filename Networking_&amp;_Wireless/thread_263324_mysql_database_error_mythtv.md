---
title: "mysql database error mythtv??"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by drews_blunted on 2006-09-23
Hello, i think i may of configured mysql the wrong way.

Is there anyway to erase anything mysql knows and restart/reconfigure it as it says in the tutorial. i must of done something wrong because when i go to localhost in my webrowser and click on phpmyadmin it says:

phpMyAdmin - Error

Cannot load mysql extension. Please check your PHP configuration. - Documentation

i keep getting this error when i run mythfilldatabase
and mythtv doesnt seem to load all my tv channels or information correctly. There is deffinatly a problem with mysql? anyone got some ideas?

DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('SH6337150000','16376','2006-10-02T19:00:00','01:00:00',0,1,0,0,0,NULL,0,0,'2006-10-02T20:00:00');
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1

^^ It says something similar to that hundreds of times over and over.

---

### Post by smit0737 on 2006-09-25
I'm getting this same error on a fresh install of Dapper Drake and mythtv 0.18 following [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) but following some updates for Dapper per [http://www.ubuntuforums.org/showthread.php?t=186747](http://www.ubuntuforums.org/showthread.php?t=186747).  I previously had mythtv 0.18 running nicely on Breezy Badger.

Thanks!

---

### Post by smit0737 on 2006-09-27
After reinstalling several mysql and phpmyadmin related packages, I eventually installed "eskuel" through synaptic.  I tried to fire it up just like phpmyadmin (set your browser to localhost and then click the link) and while it seemed to work, I got an error in another language (French?).

Anyways, I tried phpmyadmin again, and to my surprise, it worked!

Unfortunately, there is a larger problem.  It appears that Mythtv doesn't work with MySQL 5.0 yet according to this [link]("https://launchpad.net/distros/ubuntu/+source/mythtv/+bug/30593"):

The Mythtv on Ubuntu 6.06 install guide ([here]("http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation#Install_and_Configure_MySQL"))  suggests avoiding Mythtv 0.18 for this reason.

---

