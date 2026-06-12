---
title: "web server on the fly"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Patrick-Ruff on 2007-06-17
hey all, as the need arises, I need to make a temporary webserver of my laptop for home uses.  

is there any quick and easy way to do this on Ubuntu 7.04 without reinstalling the server version?

---

### Post by Schalken on 2007-06-17
Sure: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Apache is the web server. If you dont need a database, sip the MySQL part; if you dont need server scripting, skip the PHP part.

---

### Post by rich.bradshaw on 2007-06-17
In KDE there is  a kicker applet thats a drag and drop web server, very easy to set up.

---

### Post by Patrick-Ruff on 2007-06-17
thanks, I'll check it out.

---

### Post by Patrick-Ruff on 2007-06-17
apache2 doesn't appear to be working.

```
Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by minj on 2007-06-17
One easy way to get Apache2.2+PHP+MySQL working is to just install these packages:

```
sudo apt-get install apache2.2-common apache2-utils apache2-mpm-prefork libapache2-mod-auth-mysql libapache2-mod-php5 php5-common php5-mysql libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0 php5-mysql
```

Not all of them are essential, but with them it sure works on my pc. 

The next thing you want to do is 
```
sudo gedit /etc/php5/apache2/php.ini
```
find the mysql.default_socket directive and add this:
```
mysql.default_socket =/var/run/mysqld/mysqld.sock
```
then restart apache and you should be ok
```
sudo apache2 -k restart
```

EDIT:

/var/www is your document root directory. It can be changed in /etc/apache2/sites-available/default if you want. All the configuration files you might need can be found in /etc/apache2 /etc/php5 /etc/mysql directories. Note that a new user group www-data with user www-data is created. This user is used for apache server so all your documents should allow access for this user.

---

### Post by Patrick-Ruff on 2007-06-17
I sitll can't seem to get it to work.  I keep getting the same error.

---

### Post by Patrick-Ruff on 2007-06-17
anyone know?

---

### Post by avik on 2007-06-17
You are using sudo, right?  It looks like Apache isn't getting root permission to be able to do anything.

---

### Post by Patrick-Ruff on 2007-06-17
yes I am.

---

### Post by az on 2007-06-17
Skype occupies port 80.  You can't run apache with skype.

---

### Post by Patrick-Ruff on 2007-06-17
I don't use skype . . . wtf.

{the wtf was for the utter irrelevance of that statement . . .}

---

### Post by az on 2007-06-18
> **Patrick-Ruff said:**
> I don't use skype . . . wtf.

{the wtf was for the utter irrelevance of that statement . . .}

Sorry.  It's actually a common occurrence when someone tries to run a LAMP server on a desktop.  Apache cannot bind to the socket.  I got sick of going through the motions of actually asking if you were running skype....


> **Patrick-Ruff said:**
> apache2 doesn't appear to be working.

```
Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

Did you try to configure apache?  Did you install several versions of apache (apache and apache2?)  Check what apache packages you have installed.  Finally, how is your network configured?

---

### Post by Patrick-Ruff on 2007-06-21
I probably didn't configure apache.  

and I'm using this to hack a router,  I SSH'ed it and I need it to get files off of my laptop wirelessly. 

I installed ubuntu server due to my frustration.  but now I need to get X going and all this other stuff . . . so I'll probably not be trying anyhting for a while.

---

