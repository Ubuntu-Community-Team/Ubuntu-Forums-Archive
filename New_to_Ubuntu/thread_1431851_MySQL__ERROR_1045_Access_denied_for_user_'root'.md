---
title: "MySQL  ERROR 1045 Access denied for user 'root'"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by JFazenda on 2010-03-17
I lost the root password for MySQL in my Ubuntu server and have not been able to reset it with several methods I found in the forum.

I installed Ubuntu server with a Joomla website a few weeks ago. It was my first experience with Linux and I had a few problems, but was able to resolve all of them with advice I found in the forums (thanks to all participants). Everything was working until I tried to create a new database and discovered I had lost my root password for PHPmyadmin and for mysql in the ubuntu command line.

:mad: This time I'm really stuck because none of the solutions I found worked for me. I would appreciate very much any help/suggestions.

This is what happens when I use the most frequently mentioned procedure to reset the root password :

          [FONT=Verdana, sans-serif]# /etc/init.d/mysql stop[/FONT]
 [FONT=Verdana, sans-serif]* Stopping MySQL database server mysqld.[/FONT]
 

 [FONT=Verdana, sans-serif]# mysqld_safe --skip-grant-tables &[/FONT]
 [FONT=Verdana, sans-serif][1] 3845[/FONT]
 [FONT=Verdana, sans-serif]# 100316 10:06:23 mysqld_safe Logging to sislog.[/FONT]
 [FONT=Verdana, sans-serif]100316 10:06:23 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql[/FONT]
 [FONT=Verdana, sans-serif]*(did not return to ubuntu prompt but accepted next input)*[/FONT]
 

 [FONT=Verdana, sans-serif]mysql -u root[/FONT]
 [FONT=Verdana, sans-serif]Welcome to the MySQL monitor.  Commands end with ; or \g.[/FONT]
 [FONT=Verdana, sans-serif]Your MySQL connection id is 1 to server version: 5.1.37ubuntu5 (ubuntu)[/FONT]
 [FONT=Verdana, sans-serif]Type 'help;' or '\h' for help. Type '\c' to clear the buffer.[/FONT]
 [FONT=Verdana, sans-serif]mysql>[/FONT]
 

 [FONT=Verdana, sans-serif]mysql> use mysql;[/FONT]
 [FONT=Verdana, sans-serif]Reading table information for completion of table and column names [/FONT] 
 [FONT=Verdana, sans-serif]You can turn off this gfeature to get a quicker startup with -A[/FONT]
 [FONT=Verdana, sans-serif]Ctabase Changed[/FONT]
 

 [FONT=Verdana, sans-serif]mysql> update user SET password  = **'DcBa8ZyW'** where user=**'root'**;[/FONT]
 [FONT=Verdana, sans-serif]Query OK, 3 rows affected (0,00 sec)[/FONT]
 [FONT=Verdana, sans-serif]Rows **matched: 3 Changed: 3 Warnings: 0**[/FONT]
 

 [FONT=Verdana, sans-serif]mysql> flush privileges;[/FONT]
 [FONT=Verdana, sans-serif]Query OK, 0 rows affected (0,00 sec)[/FONT]
 

 [FONT=Verdana, sans-serif]mysql> quit[/FONT]
 [FONT=Verdana, sans-serif]Bye[/FONT]
 

 [FONT=Verdana, sans-serif]# /etc/init.d/mysql stop[/FONT]
 [FONT=Verdana, sans-serif]Stopping MySQL database server: mysqld[/FONT]
 [FONT=Verdana, sans-serif]STOPPING server from pid file /var/run/mysqld/mysqld.pid[/FONT]
 [FONT=Verdana, sans-serif]mysqld_safe[6186]: ended (*this output was different* )[/FONT]
 [FONT=Verdana, sans-serif][1]+  Done                    mysqld_safe --skip-grant-tables[/FONT]
 

 [FONT=Verdana, sans-serif]# /etc/init.d/mysql start[/FONT]
 

 [FONT=Verdana, sans-serif]# mysql -u root -p[/FONT]
 [FONT=Verdana, sans-serif]Password: *(typped DcBa8ZyW and repeated many times)*[/FONT]
 [FONT=Verdana, sans-serif]**ERROR 1045 (28000) : Access denied for user 'root'@'localhost' (using password YES)**[/FONT]

---

### Post by phillw on 2010-03-17
Hi, I've not tried that particular method, but have had reported success with this slight variant of it

[http://www.howtoforge.com/reset-forgotten-mysql-root-password](http://www.howtoforge.com/reset-forgotten-mysql-root-password)

Remember, you need to be the root user on your local system.

I don't usually recommend this, but in your case you'll need to issue ```
sudo -i
``` to get to the # prompt.

Once you've finished the how-to type ```
exit
``` to return to the normal $ prompt. Do be careful when at the # prompt !!!

Regards,

Phill.

---

### Post by JFazenda on 2010-03-17
Thanks for your suggestion.

/ I didn't use sudo because I log-in to ubuntu as root user (I disconnected the server from the network and internet) while trying to resolve this problem.

/ Please note that the password seems to be changed with :
[FONT=Verdana, sans-serif]mysql> update user SET password  = **'DcBa8ZyW'** where user=**'root'**;[/FONT]
[FONT=Verdana, sans-serif][COLOR=Black]**Output :**[/COLOR]
[/FONT][FONT=Verdana, sans-serif]Query OK, **3 rows affected** (0,00 sec)[/FONT]
 [FONT=Verdana, sans-serif]Rows matched: **3 Changed:** 3 Warnings: 0[/FONT]

[FONT=Verdana, sans-serif]/ If I repeat the step above with the same password 
[/FONT]**[FONT=Verdana, sans-serif]Output is :[/FONT]**
[FONT=Verdana, sans-serif]Query OK, **0 rows affected** (0,00 sec)[/FONT]
 [FONT=Verdana, sans-serif]Rows matched: **0 Changed:** 0 Warnings: 0[/FONT]
[FONT=Verdana, sans-serif]*[I guess nothing is changed because the password is the same that was already there]*
[/FONT]
[FONT=Verdana, sans-serif]/ But after I stop and restart mysql the password is rejected in:[/FONT]
 [FONT=Verdana, sans-serif]# mysql -u root -p[/FONT]
 [FONT=Verdana, sans-serif]**Output :**
[/FONT][FONT=Verdana, sans-serif]Password: *(typped DcBa8ZyW and repeated many times)*[/FONT]
 [FONT=Verdana, sans-serif]**ERROR 1045 (28000) : Access denied for user 'root'@'localhost' (using password YES)**[/FONT]
 
 I already had lots of troubles with mysql passwords when I setup ubuntu server for the first time and now I tried several different methods for resetting the password, but always with the same result:- cannot loginn neither from the command line nor from phpmyadmin.

 Looks like this is a tricky issue and, obviously, I don't know enough. I will try the method you recommended and spend more time on the manual.

---

