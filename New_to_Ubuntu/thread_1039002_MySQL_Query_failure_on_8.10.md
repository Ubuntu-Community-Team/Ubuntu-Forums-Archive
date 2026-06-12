---
title: "MySQL Query failure on 8.10"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by AmberG on 2009-01-14
Pulling my hair out on this one.
Posting here because I am certain this is an Ubuntu problem.

I have MySQL Server and MySQL Query and Emma installed and everything WAS working perfectly up until a few days ago.

MySQL 5.0.67-0ubuntu6
MySQL Client Version 5.0.67
Linux 2.6.27-11-generic

Main problem:
Run MySQL Query from menu (as before) it comes up with usual log in dialog OK when CORRECT password entered for any user (including root!) the dialog goes away but no MySQL Query browser appears. :(

Emma still works perfectly so there is no problem with passwords.
MySQLAdmin can stil be run from menu and entered and used by admin authorised users and by root.

MySQL server running ok and no other visible problems with any other application using it.

I have tried completely removing MySQL Query using the package update manager and then reinstalling it.

This does not seem to solve the problem

Any ideas or experience? Thank you


PS. maybe different problem but related - I can't seem to be able to stop the MySQL server (logged in as root) using MySQL Admin. Never had need to do this before on this machine so no idea if it ever was possible. But I can do it on Windows machine.

---

### Post by stevoo on 2009-01-14
*bump*

if you try and run it from the shell.... does it give out any errors ?

---

### Post by AmberG on 2009-01-14
> **stevoo said:**
> *bump*

if you try and run it from the shell.... does it give out any errors ?

So I posted it here because I'm "absolute beginner" on Linux
Well when it works I don't need to go any deeper.

Shell ?

Do you mean a command in terminal?
if so what command.

---

### Post by stevoo on 2009-01-14
Didnt now that ....

Anyway i havent used mysql query so it may not be the correct one

Go to applications->Accessories->Terminal
and type
mysql-query-browser
and hit enter 

See if that does anything !

---

### Post by AmberG on 2009-01-14
Thanks for responding anyway - no offence meant.

tried suggestion with following results:
```

:~$ mysql-query-browser

(mysql-query-browser:6254): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(mysql-query-browser:6254): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(mysql-query-browser:6254): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(mysql-query-browser:6254): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(mysql-query-browser:6254): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
:~$ 

```

The usual login dialog appears - when password entered then Connect'ed - terminal continues with

```

terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
:~$ 

```

and MySQL Query doesn't start. :(

---

### Post by AmberG on 2009-01-15
still no joy

anyone have any ideas other than reinstalling the server (not a pleasant idea)

---

### Post by cariboo on 2009-01-15
Remember Linux is not windows, and reinstalling will not solve your problem. Can you run queries in the mysql console?

Open a terminal and log in to the mysql console by typing the following:

```
mysql -u <user> -p <database>
```

where <user> is one of your mysql users, and <database> is the db you want to run your query on. In the console run a query to see if you get any results.

Jim

---

### Post by mapltux on 2009-01-15
try logging in and playing around with your tables/queries from the terminal

mysql --user = root --password (enter)

and then it should prompt you for the password which you would have set..

you should be inside mysql either as root or user

cheers!

Edit: Same post as cariboo907 :)

---

### Post by mapltux on 2009-01-15
Also you can try installing phpMyAdmin

its a nice interface if you do not prefer the command line

sudo apt-get install phpmyadmin

---

### Post by AmberG on 2009-01-16
Thanks cariboo907 & mapltux

mysql console works fine 
- but I cannot see how that solves the mysql-query problem ?

---------

phpMyAdmin also works - but is not what the users want - and personally I agree with them that it is very clumsy and does not work as effectively as mysql-query.

we also have emma installed - and as I stated above this works even better than phpMyAdmin - but it too has its faults and bugs.

I looked at Navicat - but that is a pile of p@@ - works great on Windows but the Linux version will not even install correctly - pretty abysmal for a commercial product - and their "support" is a flash in the pan (quick response, nothing practical)

So its back to the problem of getting mysql-query to work again

---

### Post by AmberG on 2009-01-20
Finally fixed

```
$ mv .mysqlgui .mysqlgui~ 
```

Solution courtesy of another Google search
Don't know what it does
or why it works
but certainly did the trick and MySQL-query works again

only downside spotted so far was the loss of connection definitions - no real problem there.

still no idea what caused it.

---

### Post by yknivag on 2009-01-20
I'm no expert, but my guess is that, it works by copying the config file to a different name (adds the ~ on the end) so that the program can't find it.

Chances are the program (MySQL Query) creates a default config file which has worked.

---

### Post by carlosOrozcoB on 2010-09-02
this solution:
$ mv .mysqlgui .mysqlgui~
you need to do this in your home directory, for example, if your user is carlos:
carlos@ubuntu:$mv /home/carlos/.mysqlgui /home/carlos/.mysqlgui~

in other words... just you need move the .mysqlgui to another place... and this reload the nex time that you start mysql-query-browser

...greatings

---

