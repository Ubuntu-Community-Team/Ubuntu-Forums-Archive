---
title: "Server with file sharing and also monitoring the activity"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by Rotundu_Bogdan on 2014-04-02
Ok so i'm sorry if i post in the wrong section.
I am relatively new to all that Linux means and i want to make a server for file sharing between users that uses a MySql database and i want some means to monitor it like... somewhere to show me which users logged on what did they do, reports like that.
From what i have searched and talked with some guys i understood that the way to go is Samba with MySql backend.
What i ask of you are some directions/resources. What can i read about this, how can i learn more. I want to mention that i am somewhat familiar with the windows server technology especially active directory but on the Linux side i am very new.

---

### Post by mastablasta on 2014-04-03
/var/log holds all the logs.

what will the mysql be doing? also i think mysql will probably soon be changed to mariadb in default install?!

anyway all can be done with Ubutnu server and using various packages. depending how you want to set it all up.

if you prefer GUI interface for setup and administration of server then explore Zentyal and Webmin.

SAMBA is one option. the other one is sftp. depends what the setup is. if it's a local server, what other computers use, what will you be doing on server...

also have you considered owncloud to share and sync files?

---

### Post by PartisanEntity on 2014-04-03
*Moved to Networking & Wireless*

---

### Post by Rotundu_Bogdan on 2014-04-03
Well mysql will be storing the user names and passwords mainly. I need a simple database that it's easy to understand and explain.
The other computers will be using Windows and yes it's a local server.
About owncloud, i don't need something that premade.I gotta show some fellas that i did something and learned something from it(it's more of a project).

---

### Post by apohal9 on 2014-04-03
You need something to audit which user uploaded or downloaded files from/ onto you Samba server?

---

### Post by Rotundu_Bogdan on 2014-04-03
I don't need something, i need to make something. I was thinking about a website to display some reports.
I need to make reports like what users are logged on right now,what users from a certain group were online in the last x days, what users uploaded/downloaded files etc.(i guess these events can be found in the log files).
And i need a server which i can monitor.

---

### Post by apohal9 on 2014-04-03
So then, as mastablasta sai, /var/log holds the logs, Samba or sftp is a good option, the rest is up to you ;)

---

### Post by Lars Noodén on 2014-04-03
The repository has rsyslog-mysql which should allow logging to mysql.  If you are tracking sftp usage, see the -f and -l options for [sftp-server](http://manpages.ubuntu.com/manpages/saucy/en/man8/sftp-server.8.html).  If you set the log level to INFO (and notify your users of the spying in the banner) then you can track all the uploads and downloads.  If you set the log facility to LOCAL0 or something like that you can separate out the sftp activity from the main logs.

---

