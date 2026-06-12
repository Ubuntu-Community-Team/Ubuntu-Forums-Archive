---
title: "MYSQL starting problem"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by shabaaz on 2010-08-08
i am using ubuntu 10.04 
and i want to practice some sql commands(not related to server and stuff.....just plain commands aimed at creating ,modifying tables/data base).
so i installed 
1)mysql server
2)mysql client
3)mysql navigator(donno the use of this)

now i typed "mysql -u root" in termainal hoping that something would happen(i typed it because i read it some where that i had to type it)

but then i get the error
" Access denied for user 'root'@'localhost' (using password: NO)"


WHAT TO DO NOW ....
how do i get the 
SQL> prompt





PLEASE HELP......

---

### Post by chmistry on 2010-08-08
This is not realy a ubuntu problem, but a quick google search:

try using mysql -u root -p
that will prompt you for a password

using password: NO means that you didn't supply a password

---

### Post by manObject on 2010-09-09
Setting up MySQL can be quite tricky because of the confusion between two very different levels of security. To access the mysql prompt, you need to supply the root password (that is, the Ubuntu system superuser password). Once you get the mysql prompt you can begin to set up the system-reserved **mysql ***database* tables with the details of your own, regular databases and the names of their authorised users and their passwords. *These* passwords can (and should) be different from their Ubuntu login passwords.

**MySQL Navigator** is a very useful GUI-based alternative to creating and editing MySQL databases at the command prompt. It is also an alternative to phpMyAdmin that doesn't depend on a browser. However, I must confess that I have not yet found a way of getting it to work!

---

