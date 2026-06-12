---
title: "drupal problem"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by arju305 on 2010-10-28
Guys i installed drupal6 from synaptec.
During the installation it asked me for a password to mysql. I typed it.
i restarted the apache server.
To finalize the installaion i went to........
[http://localhost/drupal6/install.php](http://localhost/drupal6/install.php)
it gives a screen with:
***************************************************************
Failed to connect to your MySQL database server. MySQL reports the following message: *Access denied for user 'drupal6'@'localhost' (using password: YES)*.
[LIST]
[*]Are you sure you have the correct username and password?
[*]Are you sure that you have typed the correct database hostname?
[*]Are you sure that the database server is running?
[/LIST]
For more help, see the [Installation and upgrading handbook]("http://drupal.org/node/258"). If you are unsure what these terms mean you should probably contact your hosting provider.
******************************************************************
 Can you tell me what is this.... and how can i overcome this problem.....
thanks........

---

### Post by AnimalMagic on 2010-10-29
You haven't got access privileges for the user to access the db from localhost. This is a mysql grant issue. Sorry I can't remember the commands to fix it (maybe GRANT?).

Either that or you're using the wrong userid/password

---

### Post by arju305 on 2010-10-29
> **AnimalMagic said:**
> You haven't got access privileges for the user to access the db from localhost. This is a mysql grant issue. Sorry I can't remember the commands to fix it (maybe GRANT?).

Either that or you're using the wrong userid/password

sorry....... but i am not getting the point..........

---

