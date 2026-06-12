---
title: "Coova Chilli Client Login Failure"
date: 2013-11-03
forum: Networking &amp; Wireless
---

### Post by okay7675 on 2013-11-03
Hi guys, I have installed coovaChilli + daloradius and freeradius as per these instructions [http://ubuntuforums.org/showthread.php?t=2070298](http://ubuntuforums.org/showthread.php?t=2070298). My clients are being redirected to the login in page- but the they cannot login using the usernames and passwords that I created in daloradius. Any login attempt returns the error message 'Username and/or password was not valid'.

I suspect it has much to do with my configuration in daloradius, but i have no idea what. I followed the instructions in the thread in the link above, but i think my version of daloradius maybe different from the one i have installed. 

Here is a copy of my /var/log/freeradius/radius.log file[INDENT=2]Sun Nov  3 16:06:59 2013 : Info: rlm_sql (sql): Closing sqlsocket 4
Sun Nov  3 16:06:59 2013 : Info: rlm_sql (sql): Closing sqlsocket 3
Sun Nov  3 16:06:59 2013 : Info: rlm_sql (sql): Closing sqlsocket 2
Sun Nov  3 16:06:59 2013 : Info: rlm_sql (sql): Closing sqlsocket 1
Sun Nov  3 16:06:59 2013 : Info: rlm_sql (sql): Closing sqlsocket 0
Sun Nov  3 16:07:00 2013 : Info: Loaded virtual server inner-tunnel
Sun Nov  3 16:07:00 2013 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded $
Sun Nov  3 16:07:00 2013 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sun Nov  3 16:07:00 2013 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sun Nov  3 16:07:00 2013 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sun Nov  3 16:07:00 2013 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@loc$
Sun Nov  3 16:07:00 2013 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'loca$
Sun Nov  3 16:07:00 2013 : Error: rlm_sql (sql): Failed to connect DB handle #0
Sun Nov  3 16:07:00 2013 : Info: Loaded virtual server <default>
Sun Nov  3 16:07:00 2013 : Info: Ready to process requests.
Sun Nov  3 16:23:41 2013 : Info: rlm_sql (sql): Trying to (re)connect unconnected handle 4..

[/INDENT]
My /var/log/daloradius.log file is empty.

I'm using Ubuntu 12.04 LTS

Any help would be greatly appreciated

---

### Post by otakugodie on 2014-02-04
Yesterday I have the same problem.

I was follow this website: [https://help.ubuntu.com/community/WifiDocs/CoovaChilli#Basic_Configuration](https://help.ubuntu.com/community/WifiDocs/CoovaChilli#Basic_Configuration)

My problem was in the connection with MySQL, more exactly on password.

I hope to help somebody.

---

