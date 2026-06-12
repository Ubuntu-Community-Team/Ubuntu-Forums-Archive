---
title: "snort installation procedures"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by shahin on 2007-04-18
Greetings-
    I am following the following link, which by the way, it rocks and have got me through most of the steps.  But as I am a beginner, I need some more details and I would like to point out some of the modifications which I have had to make so far to the procedures:
[http://ubuntuforums.org/showthread.php?t=145641&highlight=HOWTO%3A+Snort](http://ubuntuforums.org/showthread.php?t=145641&highlight=HOWTO%3A+Snort)

Item 1-
In the procedure below
mysql -u root
set password for root@localhost=password('PICK_A_PASSWORD');
create database snort;
grant insert,select on root.* to snort@localhost;
set password for snort@localhost=password('PASSWORD_SNORT_CONF');
grant create,delete,insert,select,update on snort.* to snort@localhost;
grant create,delete,insert,select,update on snort.* to snort;
exit

What does PICK_A_PASSWORD value or for that matter that statement do please?  How is this password different from PASSWORD_SNORT_CONF value in line 5 of the procedures?  
I ask this because when I was at the following step:
sansari@zamzam:/usr/share/doc/snort-mysql$ zcat create_mysql.gz | mysql -u root -h localhost -p snort
I had to type in what I put in for PICK_A_PASSWORD in line 1.  
I ask this because I feel I need to understand somewhat what I am doing here in order to configure php and apache.  I am running into another issue with php and where it installs adodb, which is an issue discussed in the thread above.  But I did not quite get what the fix is.  Even php has a message about it but for newbee like me it is somewhat vague.  Here it is:
 WARNING: include path for php has changed!                                      &#9474;
 &#9474;                                                                                 &#9474;
 &#9474; libphp-adodb is no longer installed in /usr/share/adodb. New installation path  &#9474;  
 &#9474; is now /usr/share/php/adodb.                                                    &#9474;  
 &#9474;                                                                                 &#9474;  
 &#9474; Please update your php.ini file. Maybe you must also change your web-server     &#9474;  
 &#9474; configuraton.

***********************************
The problem above is I don't know what to update in php.ini or how or what to configure in web-server.  I assume it is some file in apache as this is what we are using in the procedure.  Please advise.
Item 2-
My next problem is where we are editing the base configuration:
$Base_urlpath = “/base”
$Dblib_path = “/usr/share/adodb/”;
Change line 85 and so on to match your mysql database. Such as the username, password etc.

When I go to line 85, this is what I see:
$alert_dbname   = "mysql";
$alert_host     = "localhost";
$alert_port     = "";
$alert_user     = "snort";
$alert_password = "snort";

In above lines I changed the value in ""s to mysql, and host to localhost, I don't know what to put in for port.  I also put in snort for user and password as these are the values we used when we configured the snort.config file.   Is this correct?

Item 3-  What if I need to start over?  Do I need to undo everything I have done?  Is there procedures for this please?  I would like to say using Ubuntu has been very interesting, I have learned a lot ( based on my own standards ) and have enjoyed it alot. Thank you all for your quick reply.

Regards-

---

### Post by ustoopia on 2008-07-06
I'm having the exact same issue at the moment. Haven't been able to find a solution yet (this page was the 1st result in google)

---

