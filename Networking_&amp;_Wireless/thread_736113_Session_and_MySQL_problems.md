---
title: "Session and MySQL problems"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by Touch.Code on 2008-03-26
Hi,

I am having a couple of problems with Apache and MySQL. I have installed Webmin and have setup my MySQL databases.

I have made a PHP guestbook which relies on a database. Using Webmin I have created my databases! Now, when I try and view the guestbook it tells me:

> Fatal error: Call to undefined function mysql_connect() in /var/www/swauv-test/guestbook/library/opendb.php on line 8

I have installed mysql-server-5.

My next problem is PHP, Apache and Sessions. I made a website using PHP in windows. It has a login system requiring sessions. I installed PHP5 and the mod for apache. Now I get an error saying:

> Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /var/www/home.php:7) in /var/www/includes/headers.php on line 1

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /var/www/home.php:7) in /var/www/includes/headers.php on line 1

Even if session_start is right at the top it still gives me this error, I really need both problems to be sorted as I am a staff programmer at [Swav]("http://www.swauv.com") and I need databases and sessions for my job.

I have fixed my MySQL problems witht he Synaptic Package Manager, I just installed some missing packages.

Thankyou,
James

---

### Post by Touch.Code on 2008-03-26
I think I may have posted this in the wrong place. Could a moderator please move it? Thankyou/

---

### Post by Touch.Code on 2008-03-27
Anyone?

Just sessions. They worked under Abyss, so why not Apache?

---

