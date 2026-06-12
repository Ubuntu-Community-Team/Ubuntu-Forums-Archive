---
title: "PHP/MySQL connection not working"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by hanzi on 2006-10-15
I am trying to set up my Ubuntu Desktop to be a PHP/MySQL server.

PHP works fine. [COLOR="Blue"]mysql[/COLOR] runs from the shell if I become root. [COLOR="blue"]mysqld[/COLOR] is running.

Here is the problem: If I put this  into a PHP file:

[INDENT]$con = mysql_connect();
if (!$con)
die('Could not connect to MySQL: ' . mysql_error());
else
echo "MySQL is connected.";
[/INDENT]
I get this error:

[INDENT]Could not connect to MySQL: Access denied for user 'www-data'@'localhost' (using password: NO)[/INDENT]

What's wrong?
Thanks.

---

### Post by Jaynano on 2006-10-17
I found this

> MySQL initially only allows connections from the localhost (127.0.0.1). We'll need to remove that restriction if you wish to make it accessible to everyone on the internet. Open the file /etc/mysql/my.cnf

```
gksudo gedit /etc/mysql/my.cnf
```

Find the line bind-address = 127.0.0.1 and comment it out
...
#bind-address           = 127.0.0.1
...

on this website [http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_Database_Server]("http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_Database_Server").  I'm going to test it out and see if it helps, for I am having the same problem as you are.

---

### Post by Jaynano on 2006-10-18
You can edit the above file using vi

```
# vi /etc/mysql/my.cnf
```

in order to make changes to the file in vi you have to press "shift + i" on your keyboard.

you'll see something that looks like this if you scroll through the vi file
> # Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
 bind-address           = 127.0.0.1
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K

add a # before the seciton where it reads
>  bind-address           = 127.0.0.1


so that you disable it.
> # bind-address           = 127.0.0.1

If you're trying to connect to the database from a remote host, you may want to enable privileges to a database user to connect from that host.

connect to your default database from a shell (don't provide a database name)
```
# mysql -u *user* -p*password*
```

This next bit of code will either create a user named *user* if one does not exist, or modify the priveleges of the existing *user* for the specified *database*.  *user* will have access if he is connecting from the specified *host* and using the specified *password*.
```
mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP,
                        INDEX,ALTER, CREATE TEMPORARY TABLES, LOCK TABLES
                        ON *databasename*.*
                        TO '*db_user*'@'*host*' IDENTIFIED BY '*password*';
```

The '%' is a wild card character in mysql, so in order to have acces to the mysql server from numerous hosts, I used it in the *host* field.
```
TO 'made_up_user'@'%' IDENTIFIED BY 'made_up_password';
```

---

