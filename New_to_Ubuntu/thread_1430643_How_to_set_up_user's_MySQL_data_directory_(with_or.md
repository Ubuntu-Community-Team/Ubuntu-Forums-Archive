---
title: "How to set up user's MySQL data directory (with or without mysql-admin)?"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by ffrr on 2010-03-15
Hi all,

There's a global configuration file "/etc/mysql/my.cnf". It says the user's name is "mysql" and its data is in the directory "/var/lib/mysql". It also says:

# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.

The first option is pointless. The file exists already. So I copied it to "/home/fr/.my.cnf" and deleted everything except: 

user    = fr
datadir = /home/fr/finance

My hope was that these custom settings would override the global settings, respectively, "mysql" and "/var/lib/mysql". The instruction above, though, says: "You can copy this to *one of*", which  sounds like: you can have global settings or individual ones for each user, but not both. And, based on my experimentation, I add: if I have global settings, no user can access any data until I give him a comprehensive configuration file and delete the global one. That doesn't sound right! I must be missing a point and so my question is: how does one set up mysql users? I also add that "mysql-admin" is no help. It allows setting passwords, but no data paths. It also allows assigning privileges one by one, which looks like a side track straying off. And it warns that "etc/mysql/my.cnf" is read-only, when I don't even want to change that file.

Thanks for any suggestion.

Frederic

---

### Post by sebastianabate on 2010-03-15
> **ffrr said:**
> Hi all,

There's a global configuration file "/etc/mysql/my.cnf". It says the user's name is "mysql" and its data is in the directory "/var/lib/mysql". It also says:

# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.

The first option is pointless. The file exists already. So I copied it to "/home/fr/.my.cnf" and deleted everything except: 

user    = fr
datadir = /home/fr/finance

My hope was that these custom settings would override the global settings, respectively, "mysql" and "/var/lib/mysql". The instruction above, though, says: "You can copy this to *one of*", which  sounds like: you can have global settings or individual ones for each user, but not both. And, based on my experimentation, I add: if I have global settings, no user can access any data until I give him a comprehensive configuration file and delete the global one. That doesn't sound right! I must be missing a point and so my question is: how does one set up mysql users? I also add that "mysql-admin" is no help. It allows setting passwords, but no data paths. It also allows assigning privileges one by one, which looks like a side track straying off. And it warns that "etc/mysql/my.cnf" is read-only, when I don't even want to change that file.

Thanks for any suggestion.

Frederic

[FONT=Verdana]The purpose of the ~/.my.cnf file is only to set user specific options, it cannot overwrite the global options sets in /etc/mysql/my.cnf that affects the mysqld daemon. For example, if a user run the mysql client without any option and without a ~/.my.cnf file, the mysql client try to connect to the local system, at port 3306 as the logged user; but if the user creates a ~/.my.cnf file containing

[client]
user = another_username
password = XYZ
host = external_server
port = 13306

when the user run the mysql client without options, it connects to the host "external_server" as user "another_username" with the password "XYZ". The user "another_username" and the database "username_DB" must exist in the external_server.
[/FONT]

---

### Post by ffrr on 2010-03-16
Sebastian,

Thank you for putting me on the right track. I'm not quite there yet, though, and would appreciate a couple more hints.

It seems that I have to set up the "external-server", because just assigning the name to the variable "host" raises the error: "Unknown MySQL server host 'external_server' (1)" The port number so and so, I suspect, would also need to be defined beforehand.

The line "datadir = /home/fr/finance" makes the connection fail with the message "mysql: unknown variable "datadir=/home/fr/finance"

I am aware that I am struggling with the basics and certainly don't expect to get them spoon-fed. I'd welcome pointers to relevant reading matter.   

Frederic

---

### Post by sebastianabate on 2010-03-16
If you are just starting with MySQL, I recomend you to read the oficial reference manual at [http://dev.mysql.com/doc/refman/5.5/en/index.html](http://dev.mysql.com/doc/refman/5.5/en/index.html) (at least chapters 1 to 5).
For now you i can tell you this:
The datadir line belongs to the global /etc/my.cnf file, and sets the directory where all the databases files are stored (in Ubuntu /var/lib/mysql). When you create a database inside MySQL, a directory with the same name is created inside that directory, and contains all the files belonging to that database. You need to create users in MySQL and give them permission over an exiting database, and then the user can connect using the mysql client and create tables and insert data into it.

external_server is an example; you only need to set this option if you connect to a remote server all the time (for example, your ISP server). If you dont set the option in your ~/.my.cnf, you can pass the option in the command line

mysql --host=192.168.0.1 -u SOME_USERNAME -pSOME_USERNAME_PASSWORD

with this command you connect to the MySQL server running in the host with the IP 192.168.0.1, and you authenticate as the user SOME_USERNAME with the password SOME_USERNAME_PASSWORD.

---

### Post by ffrr on 2010-03-17
Sebastian,

Thank you very much for the info and reference to the MySQL documenation. Knowing that MySQL assigns a compulsory directory to all data saves a lot of time searching in wrong places. The documention will do nicely, I am sure. Thanks again.

Frederic

---

