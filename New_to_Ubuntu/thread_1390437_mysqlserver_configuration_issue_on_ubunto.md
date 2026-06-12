---
title: "mysqlserver configuration issue on ubunto"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by bam_usic on 2010-01-25
Hello,

I installed ubunto9.10 on my laptop and then installed apache2,php,mysql,perl.
I tested phpmyadmin on my webbrowser and it worked fine.

After that I installed an application which was developed on fedora7.
when I tried to access [http://localhost/index.php](http://localhost/index.php) it works find and when I click
any page which involved getting data from database I got following error.
################################################################################# 
Error 1045: Access denied for user 'glucose'@'localhost' (using password: YES) 
But if I then do following 
#####################################################################################
mysqld_safe --skip-grant-tables &
and then connect to php which involve to fetch data from database it works fine.
However when I click on a link which is supposed to get myphpadmin through a symbolic link admin gives me following error

############################################################


Welcome to phpMyAdmin 2.10.3

Error

MySQL said: Documentation
#2003 - Can't connect to MySQL server on '127.0.0.1' (111) 
####################################################################

This is some kind of configuration.Since I am new to this whole bunch of technology.I don't know how to get rid of these 2 probelms.
I will appreciate if you could help me to sort it out.

Thanks,
Bilal

---

### Post by cariboo on 2010-01-26
Does the user "glucose" have permission to access all the database functions? Open a terminal and type:

```
mysql -u glucose -p
```

to see if the user can access mysql.

you may have to access mysql as the root user you set up when you installed mysql and do something like this:

```
grant all privileges on *.* to glucose@'localhost'
identified by '<password>' with grant option;
```

in order for the user "glucose" to have full access.

---

