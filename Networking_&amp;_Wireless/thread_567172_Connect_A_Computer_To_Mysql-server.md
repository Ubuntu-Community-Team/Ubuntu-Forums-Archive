---
title: "Connect A Computer To Mysql-server"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by Diana Rogger on 2007-10-04
Hello Support,

I installed xubutu on a server and after that I setup a mysql database.

Next I set a mysql root password with the command: **mysqladmin -u root password newpassword**

I test if the password is working. Aswer: good

I installed a software on a windows computer to make a backup of my mysql-database and other databases that I want to setup later.

To make it posible to connect from another computer I went into the my.cnf file and I changed:

**[COLOR="Red"]bind-address = 127.0.0.1[/COLOR]** to **[COLOR="Blue"]bind-address = 192.168.50.20[/COLOR]**

192.168.50.20 is the IP of the xubuntu server where the mysql-database is installed.

The IP of the computer where the backupsoftware is installed is 192.168.50.30.


**Questions:**

1) Are the above steps enough to connect from computer 192.168.50.30 to the mysql-database (on server 192.168.50.20) ?

There is a line in the my.cnf file: **skip-external-locking**

2) What is the meaning of this line?

Thank you in advanced

Diana Rogger

---

### Post by helgman on 2007-10-04
1) From my experience that should be enough, just restart / reload the server and it should allow connections. Just make sure that the user have privileges to access the server from the IP address of the second computer.

2) It's in the [ manual](http://dev.mysql.com/doc/refman/5.0/en/server-options.html#option_mysqld_skip-external-locking).

Regards,
Helgman

---

### Post by Diana Rogger on 2007-10-04
Hi Helgman,

Thanks 4 u reply.

I log in to mysql:  **mysql -u root -p**

then I entered :  GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,INDEX,ALTER ON mysql.* 
                           TO diana@192.168.50.30 IDENTIFIED BY '123456'; 

flush privileges;
exit

After I restarted  mysql and tried to connect this message was presented to me:

Failed to connect to the MySQL server!
Error No 1045
Access denied for user 'diana'@'192.168.50.30' (using password: YES)

What did I do wrong?

Thank you in advanced.

Regards,

Diana Rogger

---

### Post by helgman on 2007-10-04
I've seen this error so many times myself but I've never documented the solution. So, you are not alone with the [Error 1045 problem](http://www.google.com/search?hl=en&q=site%3Amysql.com+Error+No+1045&btnG=S%C3%B6k&lr=). [Here](http://webyog.com/faq/23_18_en.html) is a brief explanation of what is causing the problem.

Login to the MySQL server and examine the user table. If everything is set up right there try changing the password.

I'll see if I get time to install a server tonight.

Regards,
Helgman

---

### Post by tturrisi on 2007-10-04
[http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html](http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html)

---

### Post by helgman on 2007-10-04
I don't see how the problem is solved by the link above: "Can't connect to [local] MySQL server".

As I understand it the server is on the Linux machine and backups should be made from the Windows machine, or am I missing something here? As I understand it the problem is not connecting to the MySQL server at all but connecting from the network, right?

I'm installing MySQL right now so that I can "see" what we are talking about.

Regards,
Helgman

---

### Post by helgman on 2007-10-04
I just took a "fresh" Ubuntu installation and installed the MySQL server. I then connected via the network with MySQL Query Browser and here is how I did:

Edit /etc/network/interfaces:
```
auto eth0
iface eth0 inet static
   address 192.168.1.50
   netmask 255.255.255.0
   gateway 192.168.1.1
```

Edit /etc/apt/sources.list and comment out CD. Then I installed the server and made a user:

```
apt-get update
apt-get install mysql-server
mysql -u root
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, ALTER ON mysql.* TO 'helgman'@'192.168.1.12' IDENTIFIED BY '12345';
FLUSH PRIVILEGES;
EXIT
```

Edit /etc/mysql/my.cnf and made bind-address = 192.168.1.50. Then I did a RESTART of the MySQL server (see below):

```
/etc/init.d/mysql restart
```
After that I connected to 192.168.1.50:3306 from 192.168.1.12 using helgman and 12345 and it worked like a charm.

Using the wrong password produces the 1045 error.
You can verify that the server is listening correctly by using the command:
```
netstat -t --listening
```
It should then show you the [bind-address]:mysql in the Listening Address and State LISTENING.

I was wrong about one thing, a simple reload was not enough (at least not on my server), I had to do a full restart.

Maybe you should log into the server and look at your entry in the *user* table (*mysql* database). Maybe something is wrong there.

Also note that there are a few things that differ (slightly) in my query to add the user and yours, that might be from not posting the exact command but if not maybe that is the problem (and then you should find it in the *user* table).

Does any of this help?

Regards,
Helgman

---

### Post by Diana Rogger on 2007-10-05
Hello Helgman,

Thank you very much.

I installed xubuntu on a new computer and tried to do every thing you wrote.

Results:  :)IT IS WORKINNNNNNNNNNNNNNNNNNNNNNNG :)

On the server where I already installed xubuntu did something before.
I think I should begin a next topic on the forum.
I will call it: **Cannot login to To Mysql-server**
I hope you can also help me with this topic

But on this I am very satisfied.

Thanks.

Regards,

Diana Rogger

---

