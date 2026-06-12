---
title: "Installing AMAROK and MySQL: Hand Holding Needed!"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by DaAznKnight on 2009-03-24
While starting Amarok for the first time, it says it needs to create a new database for my music. So off I went down this spiral of trying to get mySQL to work with Amarok.

Here's the installation guide for Amarok:

[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

Now, what I hate about a lot of linux guides is that they only tell you half the story. I'm still very new to the OS and don't quite understand a large portion of it.

Anywho, right now I need someone to translate the following into plain english (Not greek). I got as far as opening my.cnf in terminal (sudo). The rest is nonsense to me.

```
If your locale is UTF-8, make sure the default character set for your mqsl daemon is set up to utf8, so that all databases and tables are created with character set utf8. In Debian:

1) Edit /etc/mysql/my.cnf, adding this line to stanzas [client] and [mysqld]:

default-character-set = utf8

2) Restart the mqsql daemon to pick up the new default charset

Do this before you create the database for amarok.

Make sure the MySQL daemon is running. If necessary, add it to your linux startup scripts, via whatever method your distro uses.

Create a root password for MySQL, if you have not already done so.

$ mysql -u root 
set password for root@localhost = password('xxxxxxx'); 
flush privileges; 
quit; 

Of course change xxxxxx to the password you want.

Once you have done that, you must create a MySQL database and a user for amarok for through any usual method. You can just use the "mysql" command: (it will ask for your MySQL root password)

$ mysql -p -u root
CREATE DATABASE amarok;
USE amarok;
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';

In the above example, a database called "amarok" and a user called "amarok" were created. This user can access the database from localhost using the password "PASSWORD_CHANGE_ME". To allow access from remote hosts, use amarokuser@'%'.

It is very important that you 'GRANT ALL' privileges to user "amarok". In particular, "amarok" needs ALTER privileges on its database.

Once a database exists, open the Configure Amarok screen (found in the Settings menu), and go to the Collection tab. Change the drop-down menu from SQLite to MySQL. You will have to specify the host ("localhost" if the database is in your local box), port (3306 is the common value), and the name of the database that you have created for it ("amarok" in our example). Additionally, the username and password of a user who has write access to the given database needs to be specified (in our example, the user is "amarok", and the password is "PASSWORD_CHANGE_ME").

Remote MySQL Server Gotcha: Most MySQL installs have the daemon listening only to localhost by default.

So if you get errors about not being able to connect to the server or database, (_not_ password related errors) then you will have to edit my.cnf on the host machine (/etc/mysql/my.cnf, most likely), comment out the "bind_address" variable and restart MySQL. You may have to comment out "skip_networking", so that MySQL will listen on a tcp socket.

AFIAK there is no way of tweaking which interfaces it listens on. It listens on only 1 or on all. You should then update your firewall accordingly. 
```

Thanks in advance!

---

### Post by kanikilu on 2009-03-24
Hmm, is there a specific reason you want to use a MySQL database with it? Amarok supports SQLite as well, which is what I'm using, and I don't think it required much (if any) extra setup...

Anyways, I'll try to explain the steps the guide is requesting in more detail.

All these commands are in a terminal, so open one up: Applications > Accessories > Terminal.

First, I would recommend backing up my.cnf: ```
sudo cp /etc/mysql/my.cnf /etc/mysql/my.cnf.bak
```

Now you can open my.cnf: ```
sudo nano /etc/mysql/my.cnf
```

Use the down arrow key to find the section that starts with **[client]**. Go one line down and then press Enter/Return to create a new line, now go back up to the empty new line. Type "default-character-set = utf8" in the new line. Now repeat for the section that begins with **[mysqld]**. When you are finished, press **CTRL-X** and then **Y** and then **Enter** to save it as the same file name.

Next restart the mysql daemon/service: ```
sudo /etc/init.d/mysql restart
``` Read the output and look for any errors.

If you installed the mysql-server package from the repository, I believe it should have asked you for a root password during installation. If so, then you can skip that step of their instructions.

As far as the rest of it goes, they have the commands listed there, so I can't really explain it any better. If you have specific questions, just ask and someone will try to help.

---

### Post by DaAznKnight on 2009-03-24
That was all I needed! I didn't know WTF mysql daemon was and how to "restart" it. Amarok seems to be working just fine now too.

Thanks a lot!

EDIT: I wanted to get it on mySQL because it says it's faster. I thought "oh heck, why not".

---

### Post by BDNiner on 2009-03-24
Yeah it is a lot faster, and you can connect to the database from other computers on your network.

---

### Post by kanikilu on 2009-03-24
> **BDNiner said:**
> and you can connect to the database from other computers on your network. Ah, good point, I didn't think of that. I'll have to try that if I can ever convince my roommates to switch to Ubuntu and actually have more than one linux machine on the network :P

---

### Post by BDNiner on 2009-03-24
> **kanikilu said:**
> Ah, good point, I didn't think of that. I'll have to try that if I can ever convince my roommates to switch to Ubuntu and actually have more than one linux machine on the network :P

Yeah I also plan on setting up a media/backup server once i get some extra cash and Amarok was one of the main reason that I am even considering doing it. Very handy feature that all media players should implement.

---

### Post by hyper_ch on 2009-03-25
Amarok 1.4 or Amarok 2?

---

