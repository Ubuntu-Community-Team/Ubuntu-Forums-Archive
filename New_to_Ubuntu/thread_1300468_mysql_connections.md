---
title: "mysql connections"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by ja660k on 2009-10-25
hey guys, 
how do i allow every computer on my local network to access my mysql databases?

i ask because my ubuntu doesnt have flash and i feel like experimenting with flash & db

thanks in advance :-)

---

### Post by iMisspell on 2009-10-25
Its been a while since ive done any active-scripting... but as far as mysql goes...

First... what errors are you getting ?
What does it not do ?
You've asked a pretty broad question :)

You *might* have to do the following (depending on the version your running)...

edit: /etc/mysql/my.cnf
[ _[READ]("http://dev.mysql.com/doc/refman/5.0/en/server-options.html#option_mysqld_bind-address")_ ] bind-address = 0.0.0.0
Ive personally tried to set a range (0.0.0.0 is "open, any ip"), but never got it to work.

Then run the following
```
$mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'desiredpassword';
```

**'root'**@**'%'**
The **'root'** part is the mysql username which you will be using to connect with
The **'%'** is a wild-card so you can connect from any IP ('192.168.0.**%'** will work too)
Pretty sure the default would be **'root'**@**'localhost'**, being localhost (or 127.0.0.1) you would have a problem when trying to connect to the mysql-server from any other mahine.
'desiredpassword' needs to be changed....

More info:
[bind-address 0.0.0.0 "GRANT+ALL+PRIVILEGES"]("http://www.google.com/webhp#q=bind-address+%3D+0.0.0.0+"GRANT+ALL+PRIVILEGES"")

Good luck...

_

---

### Post by ja660k on 2009-10-25
that did it, the bind-address = 0.0.0.0
it was set to my local 127.0.0.1... it works now :-)
thanks alot.

---

### Post by iMisspell on 2009-10-25
your welcome

---

