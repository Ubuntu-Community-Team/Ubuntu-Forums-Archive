---
title: "how do i gain access to mysql in terminal?"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by kapi on 2010-04-21
How do I get to mysql to practice in the local machine before I do the stuff for real in my work.

To be honest I'm thrown in at the deep end and am a bit concerned I'll knacker something.

The mysql at work is all command line and has no gui like phpmyadmin so I'm re learning a few things.

If anyone can help I will be eternally grateful

Thanks

---

### Post by achase79 on 2010-04-21
the mysql command will start the mysql client

---

### Post by kapi on 2010-04-21
no it's not working,

 I input mysql and receive the error message access denied for user on localhost

---

### Post by achase79 on 2010-04-21
obviously the mysql client is installed.  I don't use it very much so use the "man mysql" command to get more info

---

### Post by kapi on 2010-04-21
Yes it is, I use mysql in conjunction with phpmyadmin

---

### Post by indytim on 2010-04-21
Use phpMyAdmin and make it easy(ier) on yourself starting off.

IndyTim

---

### Post by _0R10N on 2010-04-21
```
/etc/init.d/mysql status
``` will tell you whether the service is running or not.

If it's running then I guess your problem is that the user you're using is not appropiate configured to access mysql. That's because during the installation process only the "root" user is configured. So, you should run something like
```
mysql --user=root --password=password_entered_during_installation
```

Kind regards!

_0R10N >>

---

### Post by _0R10N on 2010-04-21
If MySQL never asked you for a password, then

```
mysql --user=root
``` should work!


_0R10N >>

---

### Post by zacktu on 2010-04-21
If you have a password, you're not prompted for it, so type

mysql --user=<myusername> --password=<mypassword>

with no spaces on either side of the =.

---

### Post by kapi on 2010-04-21
Where am I typing the mysql command in the terminal?

PhPmyadmin works fine and prompts me for a user name and password.

I usually go in as root user

just cant seem to gain access via the terminal, maybe I'm accessing it in the wrong place

---

### Post by _0R10N on 2010-04-21
> **kapi said:**
> no it's not working,

 I input mysql and receive the error message access denied for user on localhost

I thought that you were trying to connect to MySQL through the command line. So, that's where you should type the commands mentioned above. I also prefer phpMyAdmin, but you can also try MySQL Administrator and MySQL Query Browser, both available on the repositories.

Kind regards!


_0R10N >>

---

### Post by xumuk37 on 2010-04-21
try with...
```
sudo mysql -u[user] -p[password]
```

---

### Post by wojox on 2010-04-21
Just open a terminal and type:

```
mysql -u root -p
```

Hit enter key and it will prompt you for the password. If that doesn't work we may need to reset your root password.

---

### Post by kapi on 2010-04-22
_SOLVED!!!_ Thanks to you all - you're fantastic

Was inputting an incorrect command should have been this:

craig@craig-laptop:~$ _mysql -u root -p_

then I get a prompt for the mysql root password

Enter password: 

this then provides a message and success!!!

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 152
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

---

### Post by Drenriza on 2010-04-22
I dont rly get why you wanna use the CLI. Unless your on a server with no desktop-manager.
 
When i had my server, i used it with joomla. mysql. php5, apache2.
 
after i had installed mysql and setup a root & normal user, along with a database inside the mysql.
I installed phpmyadmin, configured it.
 
Then i closed the lid on the server (laptop) placed it under my desk ( so i codent see nor hear it ) and then i would use my normal computer to ssh to the server and use myphpadmin over my normal browser as the localhost 127.0.0.1 or something like that.
 
1000 times easier.
 
Then from their i installed all the other services.

---

### Post by _0R10N on 2010-04-22
> **kapi said:**
> _SOLVED!!!_ Thanks to you all - you're fantastic

Was inputting an incorrect command should have been this:

craig@craig-laptop:~$ _mysql -u root -p_

then I get a prompt for the mysql root password

Enter password: 

this then provides a message and success!!!

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 152
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

You're welcome. Remember that there's a lot of tools for MySQL that you can apt-get install :guitar:

Kind regards!

_0R10N >>

---

