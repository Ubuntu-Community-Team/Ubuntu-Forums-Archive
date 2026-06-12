---
title: "sql error? worpress error? what else could be?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by WestCity on 2009-10-24
Hi, I am using LAMP+WordPress. Until I had only one WordPress install in /var/www, witch was using "wordpress" db, everything was fine. Now I need to use one more db ("wordpress2"). I have tried 2 ways to use it:

1. I just simply edited wp-config.php and changed db name "wordpress" to "wordpress2". Now if I type [http://localhost/wordpress/](http://localhost/wordpress/) in Firefox, I see only index page without any grafic interface. I see only some text, hyperlinks, etc. And if i press any hyperlink, page "404" appears. Btw, I can't see "log into administration panel".

2. I downloaded fresh WordPress and saved it as WordPress2 in var/www. If I try to run install on Firefox, it says something about "can't create, you must edit config manualy". So I edited wp-config.php: wrote "wordpress2" and filled other necessary lines. Now, then I type [http://localhost/wordpress2/](http://localhost/wordpress2/) in Firefox, I see absolutely nothing. No errors, just plain white page. If I press to show source code, I get nothing, only emty space again. No single line of code...

I think wordpress2 db has no errors, and there are a lot of code in it. Why I can't see it? Any ideas?

---

### Post by WestCity on 2009-10-24
I forgot to write: wordpress.sql - 1.8 MB and wordpress2.sql - 5.4 MB. I know MySql has max 2MB upload by default, so i've edited /etc/php5/apache2/php.ini and made max 8MB.

Maybe I must do more things to get this db working?..

---

